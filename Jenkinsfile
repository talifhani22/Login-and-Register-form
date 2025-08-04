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
                sh 'truncate -s 0 logfile.log'
            }
        }
       
        
        stage('Write and Read File') {
            steps {
                script {
                    writeFile file: 'groovy1.txt', text: 'Working with files the Groovy way is easy.'
                }
                sh 'ls -l groovy1.txt'
                sh 'cat groovy1.txt'
            }
        }

    }
}
