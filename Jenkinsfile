pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/technica123/jenkins-demo.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                withCredentials([sshUserPrivateKey(
                    credentialsId: 'ec2-ssh-key',
                    keyFileVariable: 'SSH_KEY'
                )]) {
                    sh '''
    chmod 600 "$SSH_KEY"
    ansible-playbook -i inventory.ini playbook.yaml \
        --private-key "$SSH_KEY" -u ubuntu
'''
                }
            }
        }
    }
}
