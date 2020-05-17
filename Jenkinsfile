pipeline {
    agent none
    environment {
        ENV_DIR = '/root/env/'
    }
    stages {
        stage('Test-Build') { 
            agent {
                docker {
                    image 'python:3.7' 
                    args '--link=demo --network=website -p 8088:8000 -dit --name=web_demo'
                }
            }
            steps {
                sh 'echo "what?"'
                // sh 'pip install -r requirements.txt' 
                // sh 'python manage.py makemigrations'
                // sh 'python manage.py migrate'
                // sh 'uwsgi --ini /home/Documents/GitHub/website/uwsgi.ini'
            }
        }
        stage('Push-Build') { 
            agent any
            steps {
                sh '''
                    virtualenv ${ENV_WEBSITE}/website
                    source ${ENV_WEBSITE}/website/bin/activate
                    pip list
                    pip install -r requirements.txt
                    pip list
                    echo ${ENV_WEBSITE}
                '''
                // sh 'uwsgi --ini /home/Documents/GitHub/website/uwsgi.ini'
                // uwsgi --ini /home/Documents/GitHub/website/uwsgi.ini
            }
        }
    }
}