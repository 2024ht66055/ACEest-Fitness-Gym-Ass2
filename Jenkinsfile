pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "2024ht66055/appv2:v2"
        SONAR_HOST_URL = "http://localhost:9000"
        SONAR_PROJECT_KEY = "appv2"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKER_IMAGE} ."
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh """
                docker run --rm \
                -v "${WORKSPACE}:/app" \
                -w /app \
                ${DOCKER_IMAGE} \
                pytest --cov=appv2 --cov-report=xml
                """
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {

                        sh """
                        docker run --rm \
                        --network=host \
                        -e SONAR_HOST_URL=${SONAR_HOST_URL} \
                        -e SONAR_TOKEN=\$SONAR_TOKEN \
                        -v "${WORKSPACE}:/usr/src" \
                        sonarsource/sonar-scanner-cli \
                        -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                        -Dsonar.projectName=appv2 \
                        -Dsonar.sources=/usr/src \
                        -Dsonar.python.coverage.reportPaths=/usr/src/coverage.xml \
                        -Dsonar.working.directory=/tmp/sonar
                        """
                    }
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {

                    sh """
                    echo \$DOCKER_PASS | docker login -u \$DOCKER_USER --password-stdin
                    docker push ${DOCKER_IMAGE}
                    """
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline SUCCESS"
        }
        failure {
            echo "Pipeline FAILED - check logs"
        }
    }
}
