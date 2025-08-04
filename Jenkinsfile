pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/talifhani22/Login-and-Register-form.git'
        GIT_CREDENTIALS_ID = 'test_git'
        LOG_FILE = 'talifhani22/Login-and-Register-form/logfile.log'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git credentialsId: "${GIT_CREDENTIALS_ID}", url: "${GIT_REPO}", branch: 'master'
            }
        }
        stage('Clear logs') {
            steps {
                script {
                    def logPath = "${LOG_FILE}"
                    if (fileExists(logPath)) {
                        writeFile file: logPath, text: ''
                        echo "Cleared contents of ${logPath}"
                    } else {
                        echo "File ${logPath} does not exist. Creating it."
                        writeFile file: logPath, text: ''
                    }
                }
            }
        }   
    }
}
