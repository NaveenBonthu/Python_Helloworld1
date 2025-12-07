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
                sh 'pip install -r requirements.txt'

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