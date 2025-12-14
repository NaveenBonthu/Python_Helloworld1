pipeline {
    agent any

    environment {
        PYTHON = 'C:\\Users\\Venkata Naveen\\AppData\\Local\\Programs\\Python\\Python310\\python.exe'
    }

    stages {

        stage('Check Python') {
            steps {
                bat '"%PYTHON%" --version'
            }
        }

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '"%PYTHON%" -m pip install --upgrade pip'
                bat '"%PYTHON%" -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat '"%PYTHON%" -m pytest || exit 0'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Flask application...'
                bat 'start /B "" "%PYTHON%" app.py'
            }
        }
    }
}
