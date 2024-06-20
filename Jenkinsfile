pipeline {
    agent any
    environment {
    PASSWORD = "bighairycheese"
    DBNAME = "limpbizkit"
    }
    stages {
        stage('Create Secret & DB') {
            steps {
                sh "sed -e  's,{{PASSWORD}},bighairycheese ,g;' -e 's,{{DATABASE}},limpbizkit,g;' secrets.yaml"
                sh "kubectl apply -f secret.yaml"


            }
        }
        stage('Deploy Flask-App') {
            steps {
                sh "kubectl apply -f flask-app.yaml"
            }
         }
        stage('Deploy NGINX') {
            steps {
                sh "kubectl apply -f nginx.yaml"
                
            }
        }
    }
}