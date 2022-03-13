pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh """
                    cd simple_webserver
                    aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 352708296901.dkr.ecr.us-east-2.amazonaws.com
                    docker build -t flask-roman .
                    docker tag flask-roman:latest 352708296901.dkr.ecr.us-east-2.amazonaws.com/flask-roman:latest
                    docker push 352708296901.dkr.ecr.us-east-2.amazonaws.com/flask-roman:latest
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