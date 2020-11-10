pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        git(url: 'https://github.com/irvinstone/ws-biblioteca', branch: 'master')
        sh 'docker-compose -v'
      }
    }

    stage('up') {
      environment {
        PATH = '$PATH:/usr/local/bin'
      }
      steps {
        sh '''curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
'''
        sh 'chmod +x /usr/local/bin/docker-compose'
        sh 'docker ps'
        sh 'docker-compose -v'
      }
    }

    stage('BuildApp') {
      steps {
        sh 'docker-compose up -d'
      }
    }

  }
}