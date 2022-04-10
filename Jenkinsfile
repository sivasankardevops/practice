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
        stage('Docker stop') {
            steps {
                sh 'docker rm -f siva12'
                sh 'docker rmi siva12:latest'
            
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t siva12:${env.BUILD_NUMBER} .'
            
            }
        }
        stage('Docker Run') {
            steps {
                sh 'docker run -it -d -p 83:80  --name siva12 siva12:${env.BUILD_NUMBER}'
            
            }
        }
    }
}
