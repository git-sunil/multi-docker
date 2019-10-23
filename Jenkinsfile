pipeline {
  agent {
    docker {
      args '-f ./client/Dockerfile.dev ./client'
      image '-t dockersunil/react-test'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'echo "build"'
      }
    }
    stage('test') {
      steps {
        sh 'echo "test"'
      }
    }
  }
}