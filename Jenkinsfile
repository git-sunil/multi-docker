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
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}