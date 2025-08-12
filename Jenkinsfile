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
                    def pattern = '2024,2023,2022,2021,2020'
                

                    
                    sh """
                        if ls $inputFile 1> /dev/null 2>&1; then
                           grep -Ev  '$inputFile' '$pattern' > cleaned.log
                           mv cleaned.log 
                        else
                           echo "error"
                        fi
                    """

                }
            }
        }

    }
}
