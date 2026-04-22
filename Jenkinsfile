pipeline {
    agent any

    stages {
<<<<<<< HEAD
        stage('Checkout') {
=======

        stage('Checkout Code') {
>>>>>>> origin/main
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
<<<<<<< HEAD
                bat 'docker build -t 2024ht66055 .'
            }
        }

        stage('Run Tests in Docker') {
            steps {
                bat 'docker run --rm 2024ht66055 pytest'
            }
        }

        stage('Archive Build Artifacts') {
=======
                bat 'docker build -t 2024ht66055/appv2:v2 .'
            }
        }

        stage('Run Unit Tests (Pytest in Docker)') {
            steps {
                bat 'docker run --rm 2024ht66055/appv2:v2 pytest'
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    bat '''
                    docker login -u %USER% -p %PASS%
                    docker push 2024ht66055/appv2:v2
                    '''
                }
            }
        }

        stage('Archive Artifacts') {
>>>>>>> origin/main
            steps {
                archiveArtifacts artifacts: '**/*', fingerprint: true
            }
        }
    }
<<<<<<< HEAD
=======

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
>>>>>>> origin/main
}
