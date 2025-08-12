pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/talifhani22/Login-and-Register-form.git'
        GIT_CREDENTIALS_ID = 'test_git'
        GIT_BRANCH = 'master'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git credentialsId: "${GIT_CREDENTIALS_ID}", url: "${GIT_REPO}", branch: "${GIT_BRANCH}"
            }
        }
        stage('Clear logs') {
            steps {
                script{
                    
                    def inputFile = 'jboss.2025-08-*.log'
                    def tempFile = 'temp.txt'
                    def pattern = '2024'
                

                    
                    sh """
                       grep -v  '$pattern' '$inputFile'  > '$tempFile'
                       mv '$tempFile' '$inputFile'
                    """

                }
            }
        }

    }
}
