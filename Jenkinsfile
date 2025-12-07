pipeline {
    agent any
    stages{
        stage('Clone Repository') {
            steps {
                git 'https://github.com/NaveenBonthu/Python_Helloworld1.git'
            }
        }
        stage ("Install Dependencies"){
            steps {
                sh 'pip install -r requirement.txt'

            }
        }
        stage('Run Test') {
            steps {
                sh 'pytest || true'
            }
        }
        stage('Deploy') {
            steps{
                echo 'Starting Flask application..'
                sh 'nohup pyton app.py &'
            }
        }
    }
} 