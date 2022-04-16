pipeline {
    agent any    
   // environment {
   // DOCKERHUB_CREDENTIALS = credentials('dockerpswd')
  //  }
   stages {
        stage('Checkout') { 
            steps {
	      sh "rm -rf hello-world-war"
              sh "git clone https://github.com/ambareeshns/hello-world-war"
            }
        }       

stage('Build'){
	steps{
	//sh "cp /home/ubuntu/Dockerfile /var/lib/jenkins/workspace/cicd_pipeline"
	sh "cd /var/lib/jenkins/workspace/cicd_pipeline"
	sh "docker build -t build_cicd:1.0 ."
	}
}
stage('Docker hub login and publish'){
	steps{
	//sh "eho $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
	sh "docker login -u ambinsdocker -p Iquadtech@2013"
	sh "docker tag build_cicd:1.0 ambinsdocker/cicdpipeline:1.0"
	sh "docker push ambinsdocker/cicdpipeline:1.0"
	}
}
 stage('Pull and Deploy') {  
  agent { label 'tomcat' }
        steps {
        sh "docker pull ambinsdocker/cicdpipeline:1.0"
       // sh "docker rm -f por"
        sh "docker run -d -p 8090:8080 --name por ambinsdocker/cicdpipeline:1.0"
             } 
}    	   
   }
}
               
