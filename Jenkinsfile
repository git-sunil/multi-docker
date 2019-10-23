pipeline {
  agent {
    docker {
      image 'dockersunil/react-test'
    }

  }
  stages {
    stage('before_install') {
      steps {
        sh 'docker build -t dockersunil/react-test -f ./client/Dockerfile.dev ./client'
      }
    }
    stage('Test Case') {
      steps {
        sh 'docker run -e CI=true dockersunil/react-test npm test -- --coverage'
      }
    }
    stage('after_success') {
      steps {
        sh '''docker build -t dockersunil/multi-client ./client
docker build -t dockersunil/multi-nginx ./nginx
docker build -t dockersunil/multi-server ./server
docker build -t dockersunil/multi-worker ./worker
'''
      }
    }
    stage('Login to Docker CLI') {
      steps {
        sh 'echo ${DOCKER_PASSWORD} | docker login -u ${DOCKER_ID} --password-stdin'
      }
    }
    stage('Push Image to DockerHub') {
      steps {
        sh '''docker push dockersunil/multi-client
docker push dockersunil/multi-nginx
docker push dockersunil/multi-server
docker push dockersunil/multi-worker'''
      }
    }
    stage('Deployment') {
      steps {
        sh 'echo "Welcome."'
      }
    }
  }
  environment {
    AWS_ACCESS_KEY = ''
    AWS_SECRET_KEY = ''
    DOCKER_ID = 'dockersunil'
    DOCKER_PASSWORD = '1978Bipin1979'
  }
}