pipeline {
    agent any

    stages {

        stage('Setup Python') {
            steps {
                sh '''
                    python3 -m venv jenkins-venv
                    ./jenkins-venv/bin/pip install --upgrade pip
                    ./jenkins-venv/bin/pip install -r requirements.txt
                    ./jenkins-venv/bin/pip install pytest pytest-cov
                '''
            }
        }

        stage('Unit Test') {
            steps {
                sh './jenkins-venv/bin/pytest'
            }
        }

        stage('Code Coverage') {
            steps {
                sh './jenkins-venv/bin/pytest --cov=app --cov-fail-under=90'
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

        stage('Create Artifact') {
            steps {
                sh '''
                   zip -r azure-devops-aks-project.zip app.py requirements.txt
                '''
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