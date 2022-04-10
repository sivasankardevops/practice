pipeline {
    agent any
    
    environment {
    GIT_COMMIT_SHORT = sh(
                script: "printf \$(git rev-parse --short ${GIT_COMMIT})",
                returnStdout: true
        )
    }

    stages {
        stage('Git') {
            steps {
               git branch: 'main', credentialsId: 'Githubsiva', url: 'https://github.com/sivasankardevops/practice.git'
            
            }
        } 
        
        stage('Docker Build') {
            steps {
                sh 'docker build -t rvsivadocker/srivani:${GIT_COMMIT_SHORT}-${BUILD_NUMBER} .'
            
            }
        }
          stage('Docker stop') {
            steps {
                sh 'docker rm -f siva12'
                //sh 'docker rmi rvsivadocker/srivani:${GIT_COMMIT_SHORT}-${BUILD_NUMBER}'
            
            }
        }
        stage('Docker login') {
            steps {
                sh 'docker login -u rvsivadocker -p Sankar@1993'
            
            }
        }
        stage('Docker Push') {
            steps {
                sh 'docker push rvsivadocker/srivani:${GIT_COMMIT_SHORT}-${BUILD_NUMBER}'
            
            }
        }

        stage('Docker Image remove') {
            steps {
                //sh 'docker rm -f siva12'
                sh 'docker rmi rvsivadocker/srivani:${GIT_COMMIT_SHORT}-${BUILD_NUMBER}'
            
            }
        }
        stage('Docker Run') {
            steps {
                sh 'docker run -it -d -p 83:80  --name siva12 rvsivadocker/srivani:${GIT_COMMIT_SHORT}-${BUILD_NUMBER}'
            
            }
        }
    }
}
