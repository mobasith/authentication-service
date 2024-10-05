pipeline {    
    agent any    
    tools {        
        maven 'my-maven'        
        jdk 'my-jdk'    
    }    
    stages {        
        stage('Clone') {            
            steps {
                git url: 'https://github.com/mobasith/authentication-service.git', branch: 'main'
            }        
        }        
        stage('Build') {            
            steps {
                bat "mvn clean install -DskipTests"
            }        
        }        
        stage('Test') {            
            steps {
                bat "mvn test"
            }        
        }        
        stage('Deploy') {            
            steps { 
                bat "docker rm -f auth1-container"
                bat "docker rmi -f auth1-image"
                bat "docker build -t auth1-image ."
                bat "docker run -p 8090:8090 -d --name auth1-container auth1-image"
            }        
        }        
    }
}
