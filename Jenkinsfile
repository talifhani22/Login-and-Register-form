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
        stage('Commit and Push') {
            steps {
                sh '''
                    git config user.email "masindi.talifhani22@gmail.com"
                    git config user.name "talifhani22"
                    git add logfile.log
                    git commit -m "Clear logfile.log" || echo "Nothing to commit"
                    git push origin HEAD:${GIT_BRANCH}
                '''
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
