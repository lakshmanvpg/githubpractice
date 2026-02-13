pipeline {
    agent any

    parameters {
        string(name: 'CITY', defaultValue: 'London', description: 'Enter city')
    }

    environment {
        COUNTRY = "UK"
    }

    stages {
        stage('Test Variables') {
            steps {
                script {
                    def greeting = "Welcome"

                    echo "${greeting} to ${params.CITY}, ${env.COUNTRY}"
                }
            }
        }
    }
}
