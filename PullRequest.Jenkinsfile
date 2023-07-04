pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                sh '''
                sudo apt install python3-pip -y
                pip install -r yolo5/requirements.txt
                '''
            }
        }
        stage('Yolo5 - Unittest') {
            steps {
                sh '''
                cd yolo5
                python3 -m pytest --junitxml results.xml tests
                '''
            }
        }
        stage('Lint') {
            steps {
                echo "linting"
            }
        }
        stage('Functional test') {
            steps {
                echo "testing"
            }
        }
    }
}