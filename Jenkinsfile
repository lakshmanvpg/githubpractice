pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'qa', 'prod'], description: 'Select env')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building app..."
            }
        }

        stage('Deploy to Dev/QA') {
            when {
                expression { params.ENV != 'prod' }
            }
            steps {
                echo "Deploying to ${params.ENV}"
            }
        }

        stage('Production Approval') {
            when {
                expression { params.ENV == 'prod' }
            }
            steps {
                input "Approve Production?"
                echo "Deploying to Production"
            }
        }
    }
}
