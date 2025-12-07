pipeline {
    agent any
    tools {
             python 'Python3'
             }
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
                bat '"%PYTHON%" -m pip install -r requirements.txt'

            }
        }
        stage('Run Test') {
            steps {
                bat '"%PYTHON%" -m pytest || true'
            }
        }
        stage('Deploy') {
            steps{
                echo 'Starting Flask application..'
                bat 'start /B "%PYTHON%" app.py'
            }
        }
    }
} 