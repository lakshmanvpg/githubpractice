pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building..."
                sh 'exit 1'   // Change to exit 1 to test failure
            }
        }
    }

    post {
        success {
            echo "Build Success ✅"
        }
        failure {
            echo "Build Failed ❌"
        }
        always {
            echo "Pipeline Finished"
        }
    }
}
