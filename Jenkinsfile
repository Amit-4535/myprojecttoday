pipeline {
  agent any

  stages {
    stage('Copy Playbook to Ansible Master') {
      steps {
        sshagent (credentials: ['ansible-ssh-key']) {
          sh '''
            echo "Copying playbook to Ansible master..."
            scp -o StrictHostKeyChecking=no apache2.yml ansible@52.0.8.178:/tmp/apache2.yml
          '''
        }
      }
    }

    stage('Run Playbook from Ansible Master') {
      steps {
        sshagent (credentials: ['ansible-ssh-key']) {
          sh '''
            echo "Running playbook on Ansible master..."
            ssh -o StrictHostKeyChecking=no ansible@52.0.8.178 \
            "ansible-playbook /tmp/apache2.yml -i /etc/ansible/hosts"
          '''
        }
      }
    }
  }
}

