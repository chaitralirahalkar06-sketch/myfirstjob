pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'echo Build completed'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo Test completed'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying application...'
                sh 'echo Deployment completed'
            }
        }
    }

    post {

        always {
            echo 'Archiving test reports...'
            archiveArtifacts artifacts: 'test-results/*.xml',
                             allowEmptyArchive: true
        }

        success {
            echo 'Build completed successfully!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
