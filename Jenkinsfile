pipeline {
    agent any

    stages {

<<<<<<< HEAD
=======
        stage('Clone Repository') {
            steps {
                git 'https://github.com/2024ht66055/ACEest-Fitness-Gym-Ass2.git'
            }
        }

>>>>>>> 33eb423f0a502b6e783a25ad02926318e706a8bf
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
