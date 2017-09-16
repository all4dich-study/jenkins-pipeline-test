pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                parallel first: {
                    node('master'){
                    echo env.NODE_NAME
                    }
                },
                second: {
                    node('agent1'){
                    echo env.NODE_NAME
                    }
                }
            }
        }
    }
}
