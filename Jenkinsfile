pipeline {
    agent any

    stages {


        stage('Checkout') {
            steps {
                checkout scm

        stage('Install Dependencies') {
            steps {
                bat 'py -m pip install -r requirements.txt'


        stage('Checkout') {
            steps {
                checkout scm

            }
        }

        stage('Build Docker Image') {
            steps {

                bat 'docker build -t 2024ht66055 .'
            }
        }

        stage('Run Tests in Docker') {
            steps {
                bat 'docker run --rm 2024ht66055 pytest'


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
            }
