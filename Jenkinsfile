pipeline {
  agent {
    docker {
      image 'python:3.5.1'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'python --version'
        sh 'docker ps'
      }
    }

    stage('clone') {
      steps {
        git(url: 'https://github.com/irvinstone/ws-biblioteca', branch: 'master')
      }
    }

    stage('up') {
      environment {
        PATH = '$PATH:/usr/local/bin'
      }
      steps {
        sh 'docker ps'
        sh 'docker-compose -v'
      }
    }

  }
}