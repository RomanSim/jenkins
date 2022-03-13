pipeline {
    agent any
    environment {
        REGISTRY_URL = '352708296901.dkr.ecr.us-east-2.amazonaws.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh """
                    cd simple_webserver
                    aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin $REGISTRY_URL
                    docker build -t flask-roman:$BUILD_NUMBER .
                    docker tag flask-roman:$BUILD_NUMBER $REGISTRY_URL/flask-roman:$BUILD_NUMBER
                    docker push $REGISTRY_URL/flask-roman:$BUILD_NUMBER
                """
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}