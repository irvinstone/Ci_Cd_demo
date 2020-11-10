pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        git(url: 'https://github.com/irvinstone/ws-biblioteca', branch: 'master')
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