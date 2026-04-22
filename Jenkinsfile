pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t 2024ht66055/appv1:v1 .'
            }
        }

        stage('Run Unit Tests (Pytest in Docker)') {
            steps {
                bat 'docker run --rm 2024ht66055/appv1:v1 pytest'
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                                                  usernameVariable: '2024ht66055',
                                                  passwordVariable: '123456789')]) {
                    bat '''
                    docker login -u %USER% -p %PASS%
                    docker push 2024ht66055/appv1:v2
                    '''
                }
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
}
