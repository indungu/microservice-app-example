pipeline {
  agent any
  stages {
    stage('build images') {
      steps {
        sh 'docker-compose build'
      }
    }
  }
}