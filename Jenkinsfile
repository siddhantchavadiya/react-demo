pipeline {
    agent any
    
    stages {
        stage('Install dependencies') {
            steps {
                dir('frontend') {
                    // Install frontend dependencies
                    sh 'npm install'
                }
                dir('backend') {
                    // Install backend dependencies
                    sh 'npm install'
                }
            }
        }
        
        stage('Build') {
            steps {
                dir('frontend') {
                    // Build frontend
                    sh 'npm run build'
                }
            }
        }
        
        stage('Test') {
            steps {
                dir('frontend') {
                    // Test frontend
                    sh 'npm test'
                }
                dir('backend') {
                    // Test backend
                    sh 'npm test'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                dir('frontend') {
                    // Start the React frontend
                    sh 'npm run start &'
                }
                dir('backend') {
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
