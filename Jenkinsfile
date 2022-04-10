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
        stage('Docker') {
            steps {
                sh 'docker rm siva1 siva'
                sh 'docker rmi siva:latest siva1:latest'
            
            }
        }
    }
}
