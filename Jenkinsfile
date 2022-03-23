pipeline {
    agent { label 'java' }
    stages {
        stage('checkout') { 
            steps {
              sh "git clone https://github.com/ambareeshns/hello-world-war.git"
            }
        }
stage('build') { 
            steps {
              sh "mvn clean package"
            }
        }        
    }
}
