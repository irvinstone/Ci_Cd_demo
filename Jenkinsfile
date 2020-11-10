pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        git(url: 'https://github.com/xiaopeng163/docker-compose-flask', branch: 'master')
      }
    }

    stage('build') {
      steps {
        sh 'docker-compose build'
      }
    }

    stage('run') {
      steps {
        sh 'docker-compose up -d'
      }
    }

  }
}