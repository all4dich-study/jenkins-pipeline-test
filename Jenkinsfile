pipeline {
    agent  any
    stages {
        stage('first') {
            steps {
                deleteDir()
                sh 'mkdir 1 && mkdir 2'
                sh 'echo 1 > 1/out.txt'
                sh 'echo 2 > 2/out.txt'
                sh 'ps -ef > 1/process.txt'
                sh 'cat 1/process.txt'
                
            }
        }
    }
    post {
        success {
            archiveArtifacts allowEmptyArchive: true, artifacts: '1/**/*, 2/**/*'
            script {
                currentBuild.description = currentBuild.rawBuild.getLog(10)
            }
        }
    }
}
