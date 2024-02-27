pipeline {
    agent any
    
    stages {
        stage('Install dependencies') {
            steps {
                dir('client') {
                    // Install frontend dependencies
                    sh 'npm install'
                }
                dir('api') {
                    // Install backend dependencies
                    sh 'npm install'
                }
            }
        }
        
        stage('Build') {
            steps {
                dir('client') {
                    // Build frontend
                    sh 'npm run build'
                }
            }
        }
        
        stage('Test') {
            steps {
                dir('client') {
                    // Test frontend
                    sh 'npm test'
                }
                dir('api') {
                    // Test backend
                    sh 'npm test'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                dir('client') {
                    // Start the React frontend
                    sh 'npm run start &'
                }
                dir('api') {
                    // Start the Node.js backend
                    sh 'npm run dev &'
                }
            }
        }
    }
    
    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
