pipeline {
  agent any
  stages {
    stage('clone') {
      parallel {
        stage('clone') {
          steps {
            git(url: 'https://github.com/xiaopeng163/docker-compose-flask', branch: 'master')
          }
        }

        stage('error') {
          steps {
            ws(dir: '/workspace') {
              sh 'pwd && ls'
            }

          }
        }

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

    stage('test') {
      steps {
        sh 'docker run --rm --add-host host.docker.internal:host-gateway curlimages/curl curl host.docker.internal'
      }
    }

  }
}