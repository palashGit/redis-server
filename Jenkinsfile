#!/usr/bin/env groovy

pipeline {
    agent any  
    stages {
        stage('Build Redis Image') { 
            steps { 
                sh 'docker build -t ec2-3-84-52-185.compute-1.amazonaws.com:8083/redis-server:${BUILD_NUMBER} .' 
               }
        }
         stage('Nexus Login') { 
            steps { 
                sh 'docker login ec2-3-84-52-185.compute-1.amazonaws.com:8083'
               }
        }
         stage('Docker push to Nexus') { 
            steps { 
                sh 'docker tag ec2-3-84-52-185.compute-1.amazonaws.com:8083/redis-server:${BUILD_NUMBER} ec2-3-84-52-185.compute-1.amazonaws.com:8083/redis-server:latest'
               sh 'docker push ec2-3-84-52-185.compute-1.amazonaws.com:8083/redis-server:latest'
               sh 'docker push ec2-3-84-52-185.compute-1.amazonaws.com:8083/redis-server:${BUILD_NUMBER}'
            }
        }
    }
}
