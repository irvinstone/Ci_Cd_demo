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
      agent any
      environment {
        PATH = '$PATH:/usr/local/bin'
      }
      steps {
        sh '''curl -L --fail https://github.com/docker/compose/releases/download/1.27.4/run.sh -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose'''
        sh '''docker-compose -v
make -v'''
      }
    }

  }
}