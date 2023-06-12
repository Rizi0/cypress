pipeline {
  agent any
  stages {
    stage('git') {
      steps {
        git(url: 'https://github.com/Rizi0/cypress', branch: 'main')
      }
    }

    stage('terraform') {
      steps {
        sh 'terraform init'
        sh 'terraform plan'
        sh 'terraform apply -auto-approve'
      }
    }

  }
}