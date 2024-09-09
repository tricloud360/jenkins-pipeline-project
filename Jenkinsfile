pipeline {
    agent any
    environment {
        DIRECTORY_PATH = '/path/to/your/code'
        TESTING_ENVIRONMENT = 'TestingEnv'
        PRODUCTION_ENVIRONMENT = 'VincentProduction'
        RECIPIENT_EMAIL = 'tricloud360@gmail.com'  
    }
    stages {
        stage('Initial Delay') {
            steps {
                echo "Waiting for 10 seconds before starting the pipeline..."
                sleep(time: 10, unit: 'SECONDS')
            }
        }
        stage('Build') {
            steps {
                echo "Stage 1: Build"
                echo "fetch the source code from the directory path specified by the environment variable"
                echo "compile the code and generate any necessary artifacts"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Stage 2: Unit and Integration Tests"
                echo "Running unit tests and integration tests..."
            }
            post {
                success {
                    emailext subject: 'Jenkins: Unit and Integration Tests Passed',
                             body: 'The Unit and Integration Tests stage completed successfully.',
                             to: "${env.RECIPIENT_EMAIL}"
                }
                failure {
                    emailext subject: 'Jenkins: Unit and Integration Tests Failed',
                             body: 'The Unit and Integration Tests stage failed. Please check the logs.',
                             to: "${env.RECIPIENT_EMAIL}"
                }
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Stage 3: Code Quality Check"
                echo "Checking the quality of the code..."
            }
        }
        stage('Security Scan') {
            steps {
                echo "Stage 4: Security Scan"
                echo "Performing security scan..."
            }
            post {
                success {
                    emailext subject: 'Jenkins: Security Scan Passed',
                             body: 'The Security Scan stage completed successfully.',
                             to: "${env.RECIPIENT_EMAIL}"
                }
                failure {
                    emailext subject: 'Jenkins: Security Scan Failed',
                             body: 'The Security Scan stage failed. Please check the logs.',
                             to: "${env.RECIPIENT_EMAIL}"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Stage 5: Deploy to Staging"
                echo "Deploying the application to a testing environment specified by the environment variable..."
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Stage 6: Integration Tests on Staging"
                echo "Running integration tests on the staging environment..."
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Stage 7: Deploy to Production"
                echo "Deploying the code to the production environment using the environment variable specifying the environment name..."
            }
        }
        stage('Approval') {
            steps {
                echo "Stage 8: Approval"
                sleep(time: 10, unit: 'SECONDS')
            }
        }
    }
}