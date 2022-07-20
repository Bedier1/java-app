pipeline {
    
    agent any
    stages {
   
        stage('build image') {
            when {
                expression {
                    BRANCH_NAME == 'master'

                }
            }
            steps {
                script {

                    sh 'docker build -t mohamedbedier/javaapp:v1'
            }
            }
        }



           stage('pushing image ') {

             steps {
                script {

                   withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh " echo  $PASSWORD | docker login -u mohamedbedier --password-stdin "
                    sho 'docker push mohamedbedier/javaapp:v1'
                    }
            }
            }
        }



           stage('testing image') {
             steps {
                script {

                echo " testing image"
                sh 'docker run  -d -p 7070:8080 mohamedbedier/javaapp:v1'
            }
            }
        }
   
   
    }
}

