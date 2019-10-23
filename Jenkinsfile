pipeline {
  agent {
    dockerfile {
      filename '/client/Dockerfile.dev'
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