pipeline {
    agent none 
    stages {
        stage('Build') { 
            agent {
                docker {
                    image 'python:3-alpine' 
                }
            }
            steps {
                sh 'apk add build-base jpeg-dev zlib-dev'
                sh 'pip install -r requirements.txt' 
                sh 'python manage.py makemigrations'
                sh 'python manage.py migrate'
                sh 'python manage.py runserver'
            }
        }
    }
}