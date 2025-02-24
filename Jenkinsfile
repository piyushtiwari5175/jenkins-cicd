pipeline {
    agent any  // This means the pipeline can run on any available agent

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-8-openjdk-amd64"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the repository
                git 'https://github.com/piyushtiwari5175/jenkins-cicd.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven to build the project
                script {
                    sh './mvnw clean install'
                }
            }
        }

        stage('Unit Test') {
            steps {
                // Run unit tests
                script {
                    sh './mvnw test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy to Minikube or another environment
                script {
                    sh 'kubectl apply -f k8s/deployment.yaml'
                }
            }
        }

        stage('Clean Up') {
            steps {
                // Any cleanup steps after the build (optional)
                cleanWs()
            }
        }
    }

    post {
        always {
            // Always run this block, for example, to clean up resources
            echo 'Pipeline execution completed.'
        }
        success {
            // Actions on success (e.g., notify on Slack, email, etc.)
            echo 'Build successful!'
        }
        failure {
            // Actions on failure (e.g., notify on Slack, email, etc.)
            echo 'Build failed!'
        }
    }
}




























































































































































































































































































































































































































































































