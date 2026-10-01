pipeline {
    agent any

    stages {

        stage('Unit Test') {
            steps {
                sh 'pytest'
            }
        }

        stage('Code Coverage') {
            steps {
                sh 'pytest --cov=app --cov-fail-under=90'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage('Integration Test') {
            steps {
                echo 'Running Integration Tests...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}