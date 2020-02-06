pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -f "Dockerfile" -t iambrettstanley/grafanaxxl:latest .'
      }
    }
    stage('Publish') {
      when {
        branch '6.6'
      }
      steps {
        withDockerRegistry([ credentialsId: "docker-hub-credentials-iambrettstanley", url: "" ]) {
          sh 'docker push iambrettstanley/grafanaxxl:latest'
        }
      }
    }
  }
}
