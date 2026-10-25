pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/technica123/jenkins-demo.git'
            }
        }

        stage('Check Ansible') {
            steps {
                sh 'ansible --version'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh 'ansible-playbook -i inventory.ini playbook.yaml --syntax-check'
            }
        }
    }
}
