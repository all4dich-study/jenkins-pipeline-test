pipeline {
    agent any
    stages {
        stage('All') {
            steps {
                parallel(
                    "maven": {
                            sh 'mvn --version'
                    },
                    "nodejs": {
                            sh 'npm --version'
                    },
                    "ruby": {
                            sh 'ruby --version'
                    },
                    "python": {
                            sh 'python --version'
                    },
                    "php": {
                            sh 'php --version'
                    }
                )
            }
        }
        /*
        stage('maven') {
            agent { docker 'maven:3.3.3' }
            steps {
                sh 'mvn --version'
            }
        }
        stage('nodejs') {
            agent { docker 'node:6.3' }
            steps {
                sh 'npm --version'
            }
        }
        stage('ruby') {
            agent { docker 'ruby' }
            steps {
                sh 'ruby --version'
            }
        }
        stage('python') {
            agent { docker 'python:3.5.1' }
            steps {
                sh 'python --version'
            }
        }
        stage('php') {
            agent { docker 'php' }
            steps {
                sh 'php --version'
            }
        }
        */
    }
}
