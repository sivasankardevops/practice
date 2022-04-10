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
                git branch: 'main', credentialsId: '57d99371-2551-4ad7-aea0-b66e215ace20', url: 'https://github.com/sivasankardevops/Jenkins-terraform-setup.git'
            }
        }    
    }
}
