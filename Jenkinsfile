pipeline {
  agent any

  stages {
    stage('Copy Playbook to Ansible Master') {
      steps {
        sshagent (credentials: ['ansible-ssh-key']) {
          sh '''
            echo "Copying playbook to Ansible master..."
            scp -o StrictHostKeyChecking=no apache2-docker.yml ansible@52.0.8.178:/tmp/apache2-docker.yml
          '''
        }
      }
    }

    stage('Run Playbook from Ansible Master') {
      steps {
        sshagent (credentials: ['ansible-ssh-key']) {
          sh '''
            echo "Running Dockerized Apache playbook on Ansible master..."
            ssh -o StrictHostKeyChecking=no ansible@52.0.8.178 \
            "ansible-playbook /tmp/apache2-docker.yml -i /etc/ansible/hosts"
          '''
        }
      }
    }
  }
}

