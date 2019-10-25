pipeline{
    agent any
    stages{
        stage('Git Checkout'){
            step{
                git 'https://github.com/git-sunil/multi-docker.git'
            }
        }
        stage('before_install:'){
            step{
                sh script: 'docker build -t dockersunil/react-test -f ./client/Dockerfile.dev ./client'
            }
        }
        stage('script:'){
            step{
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