pipeline {
    agent none
    stages {
        stage('Test-Build') { 
            agent {
                docker {
                    image 'python:3.7' 
                    args '--link=demo --network=website -p 8088:8000'
                }
            }
            // agent none
            steps {
                sh 'pip install -r requirements.txt' 
                sh 'python manage.py makemigrations'
                sh 'python manage.py migrate'
                sh 'uwsgi --ini /home/Documents/GitHub/website/uwsgi.ini'
            }
        }
    }
}