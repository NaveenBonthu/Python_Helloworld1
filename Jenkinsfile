pipeline {
    agent any
    stages{
        stage('Clone Repository') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/NaveenBonthu/Python_Helloworld1.git',
                        credentialsId: '520'
                    ]]
                ])
            }
        }
        stage ("Install Dependencies"){
            steps {
                bat 'pip install -r requirements.txt'

            }
        }
        stage('Run Test') {
            steps {
                bat 'pytest || true'
            }
        }
        stage('Deploy') {
            steps{
                echo 'Starting Flask application..'
                bat 'nohup python app.py &'
            }
        }
    }
} 