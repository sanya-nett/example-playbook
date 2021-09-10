pipeline {
    agent {
      label 'ansible_docker'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/sanya-nett/example-playbook.git'
            }
        }
        stage('Ansible') {
            steps {
                sh '''
                    ansible-vault decrypt secret --vault-password-file vault_pass
                    ansible-galaxy install -r requirements.yml -p roles
                    ansible-playbook site.yml -i inventory/prod.yml
                '''
            }
        }
    }
}

