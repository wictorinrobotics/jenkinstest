pipeline {
    agent { docker { image 'wictorinrobotics/jenkinsdocker:latest' } }
    stages {
        stage('build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Test'){
            steps {
                sh 'node --version'
            }
        }
        /*stage('Deploy') {
            steps {
                
                timeout(time: 1, unit: 'MINUTES') {                
                    retry(3) {
                        sh './flakey-deploy.sh'
                    }
                }
            }
        }*/
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
