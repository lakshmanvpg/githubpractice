pipeline {
    agent any

    triggers {
        pollSCM('H/1 * * * *')
    }

    stages {
        stage('SCM Check') {
            steps {
                echo "Checking for Git changes"
                sh 'date'
            }
        }
    }
}
