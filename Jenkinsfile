node {
  stage('SCM checkout') {
    git 'https://github.com/indungu/microservices-app-example.git'
  }

  stage('Build docker images') {
    sh 'docker-compose build'
  }

  stage('login to dockerhub') {
    withCredentials([string(credentialsId: 'DOCKER_USERNAME', variable: 'DOCKER_USERNAME')]) {
    withCredentials([string(credentialsId: 'DOCKER_PASSWORD', variable: 'DOCKER_PASSWORD')]) {
      sh 'docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}'
    }
  }

  stage('Push images to dockerhub') {
    sh 'docker-compose push'
  }

  stage('deploy') {
    sh 'kubectl apply -R -f ./k8s'
  }
}