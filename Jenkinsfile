pipeline {
    agent any
    environment {
    DBPASSWD = "bighairycheese"
    DBNAME = "limpbizkit"
    }
    stages {
        stage('Create Secret & DB') {
            steps {
                sh "sed -e  's,{{PASSWORD}},'$DBPASSWD' ,g;' -e 's,{{DATABASE}},'$DBNAME',g;' secret.yaml | kubectl apply -f -"



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