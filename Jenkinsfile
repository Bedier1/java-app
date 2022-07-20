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
             

                   withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh " echo   $PASSWORD  | docker login -u $USERNAME --password-stdin "
                    sh 'docker push mohamedbedier/javaapp:last'
                    
            }
            }
        }



           stage('testing image') {
             steps {
                script {

                echo " testing image"
                sh ' docker pull mohamedbedier/javaapp:last '
               
            }
            }
        }
  
   
    }
}
