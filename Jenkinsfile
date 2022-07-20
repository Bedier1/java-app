pipeline {
    
    agent any
    stages {
   
        stage('build image') {

            steps {
               

                    sh ' docker build -t mohamedbedier/javaapp:last . '
            
            }
        }



           stage('pushing image ') {

             steps {
                script {

                   withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh " echo  $PASSWORD | docker login -u mohamedbedier --password-stdin "
                    sho 'docker push mohamedbedier/javaapp:last'
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

