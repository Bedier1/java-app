#!/usr/bin/env groovy

library identifier: 'jenkins-shared-library@master' , retriever: modernSCM(
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

                 buildingimage 'mohamedbedier/javaapp:v2'
                }
            }
        }



           stage('pushing image ') {

             steps {
                 script {

                    pushingimage 'mohamedbedier/javaapp:v2'
                   }
            }
           
        }



           stage('testing image') {
             steps {
                script {

                echo " testing image"
                sh ' docker pull mohamedbedier/javaapp:v2 '
               
            }
            }
        }
  
   
    }
}
