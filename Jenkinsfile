pipeline {
    
    agent any
    
    environment {
        imageName = "nexusone"
        registryCredentials = "admin"
        registry = "http://192.168.56.13/"
        dockerImage = ''
    }
    
     stages {
        stage('Code checkout') {
            steps {
                 git branch: 'main', url: 'https://github.com/suman7799/git_jenkins_nexus.git'
				 }
        }
		
      }
    
    // Building Docker images
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build imageName
        }
      }
    }
    // Uploading Docker images into Nexus Registry
     stage('Uploading to Nexus') {
     steps{  
         script {
             docker.withRegistry( 'http://'+registry, registryCredentials ) {
             dockerImage.push('latest')
          }
        }
      }
    }
   }
