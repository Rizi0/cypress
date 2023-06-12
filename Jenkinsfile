pipeline {
  agent any
  stages {
    stage('git') {
      steps {
        git(url: 'https://github.com/Rizi0/cypress', branch: 'main')
      }
    }

    stage('terraform install') {
      steps {
        sh 'sudo apt-get update && sudo apt-get install -y gnupg software-properties-common'
        sh '''wget -O- https://apt.releases.hashicorp.com/gpg | \\
gpg --dearmor | \\
sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
'''
        sh '''gpg --no-default-keyring \\
--keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \\
--fingerprint
'''
        sh 'sudo apt update'
        sh 'sudo apt-get install terraform'
      }
    }

    stage('terraform apply') {
      steps {
        sh 'terraform init'
      }
    }

  }
}