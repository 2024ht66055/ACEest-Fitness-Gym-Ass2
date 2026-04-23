pipeline {
    agent any

    environment {
        IMAGE_NAME = "2024ht66055/appv2:v2"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %IMAGE_NAME% ."
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat "docker run --rm %IMAGE_NAME% pytest"
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {
                        bat """
                        docker run --rm ^
                        -e SONAR_HOST_URL=http://host.docker.internal:9000 ^
                        -e SONAR_LOGIN=%SONAR_TOKEN% ^
                        -v "%WORKSPACE%":/usr/src ^
                        sonarsource/sonar-scanner-cli ^
                        -Dsonar.projectKey=gym-app ^
                        -Dsonar.sources=.
                        """
                    }
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    bat """
                    docker login -u %USER% -p %PASS%
                    docker push %IMAGE_NAME%
                    """
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