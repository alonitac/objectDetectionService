pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                sh '''
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

            post {
                always {
                    junit allowEmptyResults: true, testResults: 'yolo5/results.xml'
                }

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