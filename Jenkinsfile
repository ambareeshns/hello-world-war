pipeline {
    agent any    
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerpasswrord')
    }
   stages {
        stage('Checkout') { 
            steps {
              sh "git clone https://github.com/ambareeshns/hello-world-war"
            }
        }
stage('Maven Build') { 
            steps {
              sh "mvn clean package"
            }
        }  
        
/* stage('Copying docker file to target folder') {     
            steps {
                sh "cp /home/ubuntu/Docke*/
   }
}
               
