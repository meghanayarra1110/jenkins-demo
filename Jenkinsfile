pipeline {
    agent any

    parameters {
        choice(
            name: 'ENV',
            choices: ['dev', 'staging', 'production'],
            description: 'Select deployment environment'
        )
    }

    environment {
        APP_NAME = 'my-demo-app'
        PRACTICE_CREDS = credentials('e7eb2747-e1aa-4191-b1f4-fd0e661d08b3')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building ${APP_NAME} for ${params.ENV}"
            }
        }

        stage('Test') {
            steps {
                echo "Testing ${APP_NAME} for ${params.ENV}"
            }
        }

        stage('Create Artifact') {
            steps {
                sh 'echo "This is my Jenkins artifact" > build-output.txt'
            }
        }

        stage('Use Credentials') {
            steps {
                sh 'echo "Credential username is available to Jenkins"'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'build-output.txt'
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
