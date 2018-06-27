pipeline {
  agent any
  stages {
    stage('build images') {
      steps {
        sh 'docker-compose build'
      }
    }
    stage('upload images') {
      steps {
        sh 'docker-compose push'
      }
    }
  }
}