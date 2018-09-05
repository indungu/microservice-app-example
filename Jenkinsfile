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
        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
        sh 'docker-compose push'
      }
    }
    stage('deploy') {
      steps {
        sh 'kubectl apply -R -f k8s/'
      }
    }
  }
  environment {
    DOCKER_USERNAME = credentials("DOCKER_USERNAME")
    DOCKER_PASSWORD = credentials("DOCKER_PASSWORD")
  }
}