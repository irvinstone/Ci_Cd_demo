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

        stage('') {
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
        sh 'curl 127.0.0.1'
      }
    }

  }
}