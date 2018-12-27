#!/usr/bin/env groovy

pipeline {
    agent any  
    stages {
        stage('Build Redis Image') { 
            steps { 
                sh 'docker build -t ec2-54-173-108-195.compute-1.amazonaws.com:8083/redis-server:${BUILD_NUMBER} .' 
               }
        }
         stage('Nexus Login') { 
            steps { 
                sh 'docker login ec2-54-173-108-195.compute-1.amazonaws.com:8083'
               }
        }
         stage('Docker push to Nexus') { 
            steps { 
               sh 'docker push ec2-54-173-108-195.compute-1.amazonaws.com:8083/redis-server:${BUILD_NUMBER}'
            }
        }
         stage('Compile') { 
            steps { 
               echo 'This is a compile stage.' 
            }
        }
    }
}
