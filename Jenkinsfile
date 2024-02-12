pipeline {
    agent any

    environment {
        KUBE_CONFIG = credentials('your-kube-config-credentials-id')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Push React Docker Image') {
            steps {
                script {
                    // Build and push React Docker image
                    dir('client') {
                        docker.build("hiral12345/react_client:latest")
                        docker.withRegistry('https://index.docker.io/v1/', 'docker-hub') {
                            docker.image("hiral12345/react_client:latest").push()
                        }
                    }
                }
            }
        }

        stage('Build and Push Node Docker Image') {
            steps {
                script {
                    // Build and push Node Docker image
                    dir('api') {
                        docker.build("hiral12345/react_api:latest")
                        docker.withRegistry('https://index.docker.io/v1/', 'docker-hub') {
                            docker.image("hiral12345/react_api:latest").push()
                        }
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Use kubectl commands to deploy your application to Kubernetes
                    sh "kubectl --kubeconfig=$KUBE_CONFIG apply -f deployment.yml"
                }
            }
        }
    }
}
