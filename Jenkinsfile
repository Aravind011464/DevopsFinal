pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the Git repository
                git 'https://github.com/Aravind011464/DevopsFinal.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    docker.build('my-node-app')
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run the Docker container to execute tests
                    docker.image('my-node-app').inside {
                        sh 'npm test'
                    }
                }
            }
        }

        stage('Build Application') {
            steps {
                script {
                    // Run the Docker container to build the application
                    docker.image('my-node-app').inside {
                        sh 'npm run build'
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs() // Clean workspace after build
        }
    }
}