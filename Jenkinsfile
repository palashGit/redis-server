pipeline {
    agent any  
    stages {
        stage('Build Redis Image') { 
            steps { 
                sh 'docker login ec2-54-173-108-195.compute-1.amazonaws.com:8083'
               sh 'docker build -t ec2-54-173-108-195.compute-1.amazonaws.com:8081/redis-server:{BUILD_NUMBER} .' 
               }
        }
         stage('Docker push to Nexus') { 
            steps { 
               sh 'docker push http://ec2-54-173-108-195.compute-1.amazonaws.com:8081:${BUILD_NUMBER} .'
            }
        }
         stage('Compile') { 
            steps { 
               echo 'This is a compile stage.' 
            }
        }
         stage('Deploy') { 
            steps { 
               echo 'This is a deploy stage.' 
            }
        }
    }
}
