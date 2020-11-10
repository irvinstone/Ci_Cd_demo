pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        ws(dir: '/workdir') {
          git(url: 'https://github.com/xiaopeng163/docker-compose-flask', branch: 'master')
        }

      }
    }

    stage('build') {
      steps {
        sh 'docker-compose stop'
        sh 'docker-compose down'
        sh 'docker-compose build'
      }
    }

    stage('run') {
      steps {
        sh 'docker-compose up -d'
      }
    }

    stage('test') {
      steps {
        sh 'docker run --rm --add-host host.docker.internal:host-gateway curlimages/curl curl host.docker.internal'
      }
    }

    stage('clean') {
      steps {
        cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenSuccess: true)
      }
    }

  }
}