pipeline {
    agent {label 'siva'}
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
    }
}
