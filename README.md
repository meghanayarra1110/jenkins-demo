pipeline {
    agent any

    environment {
        APP_NAME = 'my-demo-app'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"
            }
        }

        stage('Test') {
            steps {
                echo "Testing ${APP_NAME}"
            }
        }
    }
}
