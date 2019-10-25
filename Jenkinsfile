pipeline{
    agent any
    stages{
        stage('Git Checkout'){
            steps{
                git 'https://github.com/git-sunil/multi-docker.git'
            }
        }
        stage('before_install:'){
            steps{
                sh script: 'docker build -t dockersunil/react-test -f ./client/Dockerfile.dev ./client'
            }
        }
        stage('script:'){
            steps{
                sh script: 'docker run -e CI=true dockersunil/react-test npm test -- --coverage'
            }
        }
    }
    post{
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
    }
}