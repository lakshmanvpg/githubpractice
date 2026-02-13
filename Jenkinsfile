    pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'qa', 'prod'], description: 'Select environment')
        string(name: 'VERSION', defaultValue: '1.0', description: 'Application version')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests?')
    }

    environment {
        APP_NAME = "demo-app"
        SECRET_VALUE = credentials('my-secret')
    }

    stages {

        stage('Initialize') {
            steps {
                echo "Starting Pipeline..."
                echo "Build Number: ${env.BUILD_NUMBER}"
                echo "App Name: ${env.APP_NAME}"
            }
        }

        stage('Build') {
            steps {
                echo "Building version ${params.VERSION}"
                sh 'echo Build completed'
            }
        }

        stage('Parallel Tests') {
            when {
                expression { params.RUN_TESTS == true }
            }

            parallel {

                stage('Unit Test') {
                    steps {
                        sh 'echo Running Unit Tests'
                        sh 'sleep 3'
                    }
                }

                stage('Integration Test') {
                    steps {
                        sh 'echo Running Integration Tests'
                        sh 'sleep 3'
                    }
                }

                stage('Security Scan') {
                    steps {
                        sh 'echo Running Security Scan'
                        sh 'sleep 3'
                    }
                }
            }
        }

        stage('Deploy') {
            when {
                expression { params.ENV != 'prod' }
            }
            steps {
                echo "Deploying ${params.VERSION} to ${params.ENV}"
                sh 'echo Deployment successful'
            }
        }

        stage('Production Approval') {
            when {
                expression { params.ENV == 'prod' }
            }
            steps {
                input "Approve Production Deployment?"
                echo "Deploying to Production..."
            }
        }
    }

    post {

        always {
            echo "Pipeline Finished"
        }

        success {
            echo "Pipeline Successful"
        }

        failure {
            echo "Pipeline Failed"
        }
    }
}
