pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                git branch: 'main',
                    url: 'https://github.com/chaitralirahalkar06-sketch/myfirstjob.git'
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
                sh 'mkdir -p test-results'
                sh 'echo Test completed'
            }
        }

        stage('Deploy') {
            when {
                expression {
                    env.GIT_BRANCH == 'origin/main' ||
                    env.GIT_BRANCH == 'main'
                }
            }
            steps {
                echo 'Deploying application...'
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
