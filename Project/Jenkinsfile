pipeline {
  agent any
  stages {
    stage('Terraform Init') {
      steps {
        sh 'cd terraform && terraform init'
      }
    }
    stage('Terraform Apply') {
      steps {
        sh 'cd terraform && terraform apply -auto-approve'
      }
    }
    stage('Run Ansible') {
      steps {
        sh 'ansible-playbook -i ansible/inventory.ini ansible/install_web.yml'
      }
    }
    stage('Verify') {
      steps {
        sh 'curl http://<your-vm-ip>'
      }
    }
  }
}
