pipeline {
    agent any
    
    stages {
        stage('Install dependencies') {
            steps {
                dir('client') {
                    // Install frontend dependencies
                    sh 'apt update'
                    sh 'apt install default-jre'

                    sh 'apt install npm'
                    
                }
                dir('api') {
                    // Install backend dependencies
                    sh 'apt install npm'
                    slackSend channel: 'jenkins_alert', message: 'started build job successfully '
                }
            }
        }
        
        stage('Deploy') {
            steps {
                dir('client') {
                    // Start React server
                    sh 'npm run start &'
                }
                dir('api') {
                    // Start Node.js server
                    sh 'npm run dev &'
                }
            }
        }
    }
    
    post {
        success {
            echo 'Build succeeded !!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
