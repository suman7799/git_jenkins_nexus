pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/suman7799/git_jenkins_nexus.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t nexusone:latest .' 
                sh 'docker tag nexusone admin/nexusone:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to nexus') {
            steps {
        withNexusRegistry([ credentialsId: "admin", url: "http://192.168.56.13:8081/repository/devops_private/" ]) {
           sh  'docker push admin/nexusone:$version' 
		}
                  
          }
        }
		
    }
}
