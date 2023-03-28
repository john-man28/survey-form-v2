pipeline {
  agent {
    docker {
      image 'node:latest'
    }
  }
  
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    
    stage('Build and Test') {
      steps {
        sh 'docker-compose -f docker-compose.yml up -d --build'
        sh 'docker run survey-form-v2 sh -c "npm test"'
        sh 'docker-compose -f docker-compose.yml down'
      }
    }
  }
  
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
}
