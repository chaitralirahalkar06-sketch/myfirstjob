pipeline {
  agent any

  stages {
    stage ('Checkout') {                    // Bug -1 : Moved the stage ('Checkout')  inside Stages {}
      steps {
        git url: 'https://github.com/example/app.git'     
    }

    stage ('Build') {
      steps {
        sh 'npm install'
        sh 'npm test'
      }
    }

    stage ('Parallel Tests') {
      parallel {
        stage ('Unit Tests') {            // Bug - 2 curly bracket was missing at stage ('Unit Tests')
          steps { 
            sh 'npm test' 
          }
        }

        stage ('Lint') {                  
          steps {
            sh 'npm run lint'
          }
        }
      }
    }                                    // Bug - 3 stage ('Parallel Tests') had a structural problem braces matching not complete the stage block

    post {                               // Bug - 4 the post must be outside the stages block it was inside the stage block.
      always {
        sh 'rm -rf workspace/*'
      }
    }
  }
}
        
    
