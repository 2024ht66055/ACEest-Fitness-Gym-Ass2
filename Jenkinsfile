pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/2024ht66055/ACEest-Fitness-Gym-Ass2.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirement'
                bat 'pip install pytest'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest'
            }
        }
    }
}
