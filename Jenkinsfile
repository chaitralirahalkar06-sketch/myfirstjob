pipeline {
  agent any 
    stages {
      stage ('Checkout') {
        steps {
          checkout scm
        }
      }
      stage ('Build') {
        steps {
          sh 'echo Building...'
        }
      }
      stage ('Test') {
        steps {
          sh 'echo Running Testing...'
        }
      }
      stage ('Deploy') {
        when {
          branch 'main'
        }
        steps {
          sh 'echo Deploying...'
        }
      }
    }

    post {
      always {
        sh 'echo archiving test reports'
      }
      success {
        sh 'echo The build passed'
      }
      failure {
        sh 'echo The build failed'
      }
    }
}
      
      
