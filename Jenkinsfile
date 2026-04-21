pipeline {
    agent any

    stages {


        stage('Checkout') {
            steps {
                checkout scm
=======
        stage('Install Dependencies') {
            steps {
                bat 'py -m pip install -r requirements.txt'

=======
        stage('Checkout') {
            steps {
                checkout scm

            }
        }

        stage('Build Docker Image') {
            steps {
<<<<<<< HEAD
<<<<<<< HEAD
=======
>>>>>>> 0c771672906ff0e498b520294ccd26b67a1bcdd8
                bat 'docker build -t 2024ht66055 .'
            }
        }

        stage('Run Tests in Docker') {
            steps {
                bat 'docker run --rm 2024ht66055 pytest'
<<<<<<< HEAD
=======
                bat 'py -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t fitness-app:v1 .'
>>>>>>> 5f29be2a7b7f52286bd756af1c8baa0cbcb0be13
=======
>>>>>>> 0c771672906ff0e498b520294ccd26b67a1bcdd8
            }
        }
    }
}
