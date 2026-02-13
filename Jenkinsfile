pipeline {
    agent any

    stages {
        stage('Set Variable') {
            steps {
                script {
                    env.NEW_VAR = "Dynamic Value"
                }
            }
        }

        stage('Print') {
            steps {
                echo "${env.NEW_VAR}"
            }
        }
    }
}
