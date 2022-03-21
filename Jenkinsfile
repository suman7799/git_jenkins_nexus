pipeline {
    agent any
	environment {
        imageName = "nexusone"
        registryCredentials = "admin"
        registry = "http://192.168.56.13:8081/"
        dockerImage = ''
        }

 stages {
      stage('checkout') {
           steps {
             
               git branch: 'main', url: 'https://github.com/suman7799/git_jenkins_nexus.git'
             
          }
        }
       

      stage('Docker Build') {
           steps {
              
                dockerImage = docker.build nexusone 
                
               
          }
        }
      stage('Publish image to nexus') {
            steps {
                    docker.withRegistry( 'http://192.168.56.13:8081/#browse/browse', admin ) {
                    dockerImage.push('latest') 
		         }
                  
          }
        }
		
    }
}
