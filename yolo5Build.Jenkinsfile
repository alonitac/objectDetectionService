pipeline {
    agent any

    stages {
        stage('ECR authentication and Docker login') {
            steps {
                sh '''
                aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-2.amazonaws.com
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                cd yolo5
                docker build -t alonit-yolo5 .
                '''
            }
        }

        stage('Push to ECR') {
            steps {
                sh '''
                docker tag alonit-yolo5:latest 854171615125.dkr.ecr.us-east-2.amazonaws.com/alonit-yolo5:0.0.${BUILD_NUMBER}
                docker push 854171615125.dkr.ecr.us-east-2.amazonaws.com/alonit-yolo5:0.0.${BUILD_NUMBER}
                '''
            }
        }
    }
}