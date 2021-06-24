
pipeline {
    
    environment {
    imagename = "BecomeDevops/petclinic"
    registryCredential = 'Dockerhubcreds'
    dockerImage = ''
  }
    agent any

    stages {
        
        
        
        stage('git') {
            steps {
                echo 'clonning Repository'
                git branch: 'main', url: 'https://github.com/mnagen/spring-petclinic.git'
                
                echo 'Repo clone successfully'
            }
            
        }
        
        
       stage('BUILD') {
            steps {
                echo 'Build the code'
                sh './mvnw package'
            }
       }
            
            
            
            
            stage('DEPLOY') {
            steps {
                echo 'Deploy the code'
                
                script {
                  dockerImage = docker.build imagename
                  
                }
            } 
                
            }  
            
            
            stage('push') {
            steps {
                echo 'Deploy the code'
                script{
                    
                 docker.withRegistry( '', registryCredential ) {
                  dockerImage.push("$BUILD_NUMBER")
                  dockerImage.push('latest')
                 }}

          }
                
                
                
                
            }
        } 
        
        
        
        
        
        
        
    }
    
    

