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
	sh "docker build -t build_cicd:${BUILD_NUMBER} ."
	}
}
stage('Docker hub login and publish'){
	steps{
	//sh "eho $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
	sh "docker login -u ambinsdocker -p Iquadtech@2013"
		sh "docker tag build_cicd:${BUILD_NUMBER} ambinsdocker/cicdpipeline:${BUILD_NUMBER}"
	sh "docker push ambinsdocker/cicdpipeline:${BUILD_NUMBER}"
	}
}
stage('Deploy') {  
  agent { label 'kuber' }
        steps {
        
        //sh "docker pull anilpu3/cicd-build-docker-repo:${BUILD_NUMBER}"
        //sh " cd /root "
        // sh " sed -i '25s/tomcat:latest/tomcat:9.0/Ig' /root/deployment.yml "      
        sh " kubectl apply -f /root/deployment.yml"
        sh " kubectl get pod "
        sh " kubectl get deployment "
        sh " kubectl get pod "
        sh " kubectl apply -f /root/tomcat_nodeportsvc.yml "
sh " kubectl get svc "
        // sh "docker rm -f port"
        // sh "docker run -d -p 9090:8080 --name port anilpu3/cicd-build-docker-repo:${BUILD_NUMBER}"
             } 
}    
}
}
