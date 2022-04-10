pipeline {
    agent any    
   // environment {
   // DOCKERHUB_CREDENTIALS = credentials('dockerpswd')
  //  }
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
        
stage('Copying docker file to target folder') {     
            steps {
                sh "cp /home/ubuntu/Dockerfile /var/lib/jenkins/workspace/cicd_pipeline/target"
		}
	}
stage('Build Docker Image'){
	steps{
	sh "docker build -t build_cicd:1.0 /var/lib/jenkins/workspace/cicd_pipeline/target"
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
   }
}
               
