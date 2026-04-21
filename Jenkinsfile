pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'py -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'py -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t fitness-app:v1 .'
            }
        }
    }
}
