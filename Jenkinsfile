pipeline {
    agent any

    parameters {
        choice(
            name: 'ENV',
            choices: ['dev', 'staging', 'production'],
            description: 'Select deployment environment'
        )
    }

    stages {
        stage('Build') {
            steps {
                echo "Building application for ${params.ENV}"
            }
        }

        stage('Test') {
            steps {
                echo "Testing application for ${params.ENV}"
            }
        }

        stage('Create Artifact') {
            steps {
                sh 'echo "This is my Jenkins artifact" > build-output.txt'
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
