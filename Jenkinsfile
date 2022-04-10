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
                sh 'docker build -t siva111:latest .'
            
            }
        }
        stage('Docker Run') {
            steps {
                sh 'docker run -it -d -p 82:80  --name siva111 siva111:latest'
            
            }
        }
    }
}
