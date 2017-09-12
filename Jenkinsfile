pipeline {
  agent {
    node {
      label 'master'
    }
    
  }
  stages {
    stage('Clean') {
      steps {
        parallel(
          "Clean": {
            sh 'rm -rf ./test'
            
          },
          "Clean_check": {
            sh 'ls -al'
            
          },
          "Print Messsage": {
            echo 'Hello world'
            
          }
        )
      }
    }
    stage('Clone') {
      steps {
        sh 'git clone https://github.com/all4dich/jenkins-manager-groovy.git ./test'
      }
    }
    stage('Browse') {
      steps {
        sh 'ls -al'
        sh 'pwd'
      }
    }
  }
}