pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/talifhani22/Login-and-Register-form',branch: 'master'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                echo 'Clearing log file contents using Ansible...'
                sh '''
                    export ANSIBLE_LOG_PATH=./ansible.log
                    ansible-playbook -i inventory.yml test.yml
                '''
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
        success {
            echo 'Log file cleared successfully.'
        }
    }
}
