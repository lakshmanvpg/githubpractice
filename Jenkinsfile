pipeline {
    agent any

    stages {
        stage('Retry Example') {
            steps {
                retry(3) {
                    sh 'exit 1'
                }
            }
        }
    }
}
