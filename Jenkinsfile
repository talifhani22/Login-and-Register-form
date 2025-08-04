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
                sh 'rm -f groovy1.txt'
            }
        }
       
        
        stage('Write and Read File') {
            steps {
                script {
                    writeFile file: 'groovy2.txt', text: 'Working with files the Groovy way is easy.'
                }
                sh 'ls -l groovy2.txt'
                sh 'cat groovy2.txt'
            }
        }

    }
}
