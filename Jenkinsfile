pipeline {
    agent any

    environment {
        ANSIBLE_INVENTORY = 'inventory.yml' // Path to your Ansible inventory file
        ANSIBLE_PLAYBOOK = 'playbook.yml'  // Path to your Ansible playbook
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code...'
                git url: 'https://github.com/talifhani22/Login-and-Register-form',branch: 'master'
            }
        }

        stage('Install Ansible') {
            steps {
                echo 'Installing Ansible...'
                sh '''
                if ! command -v ansible &> /dev/null; then
                    sudo apt update
                    sudo apt install -y ansible
                fi
                '''
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                echo 'Running Ansible playbook...'
                sh """
                ansible-playbook -i ${ANSIBLE_INVENTORY} ${ANSIBLE_PLAYBOOK}
                """
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
