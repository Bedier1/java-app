#!/usr/bin/env groovy

library identifier: 'jenkins-shared-library@main' , retriever: modernSCM(
    [$class: 'GitSCMSource' ,  
     remote: 'https://github.com/Bedier1/jenkins-shared-library'
     ]
)



pipeline {
    
    agent any
    stages {
   
        stage('build image') {

            steps {
                script {

                 buildingimage 'mohamedbedier/javaapp:v3'
                }
            }
        }



           stage('pushing image ') {

             steps {
                 script {

                    pushingimage 'mohamedbedier/javaapp:v3'
                   }
            }
           
        }



           stage('testing image') {
             steps {
                script {

                echo " testing image"
                sh ' docker pull mohamedbedier/javaapp:v3 '
                sh ' docker run -d   mohamedbedier/javaapp:v3 '               
            }
            }
        }
  
   
    }
}
