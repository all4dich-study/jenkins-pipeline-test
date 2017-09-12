pipeline {
    agent {
        label 'master'
    }
    
    stages {
        stage('Clean') {
            steps {
                sh 'rm -rf ./test'
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