pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                parallel first: {
                    echo 'first' 
                },
                second: {
                    echo 'second'
                }
            }
        }
    }
}
