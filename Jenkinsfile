pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'qa', 'prod'], description: 'Select env')
    }

    stages {

        stage('Build') {
            steps {
                echo "Building..."
            }
        }

        stage('Approval for Prod') {
            when {
                expression { params.ENV == 'prod' }
            }
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    input message: "Approve Production Deployment?"
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV}"
            }
        }
    }
}
