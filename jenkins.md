```

pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven_Home"
    }

    stages {
        stage('Clone') {
            steps {
                // Get some code from a GitHub repository
                echo "Cloning from github"
                git url:'https://github.com/sagar-iitg/SecureGate.git', branch:'dev'
                
            }
        }    
                
        stage('Clean') {
            steps {
                
                echo "Cleaning the project..."
                sh "mvn clean"
            }    
        }
        // stage('Test') { 
        //     steps {
        //         echo "Testing the new build..."
        //         sh "mvn test"
                
        //     } 
        // }
        
        stage('Package') { 
            steps {
                echo "Packaging the new build..."
                sh "mvn package"
        
            }
            
        }        
        
        // stage('Docker Compose Down') { 
        //     steps {
        //         echo "Deploy the new build..."
        //         bat "docker-compose down"
        //         // bat "npx kill-port 8080"
        //         // sleep 10
        //     } 
        // }
        
        // stage('Docker Compose up') { 
        //     steps {
        //         echo "Deploy the new build..."
        //         bat "docker-compose up -d"
                
        //     } 
        // }
        
        // stage('keycloak ') { 
        //     steps {
        //         echo "Deploy the new build..."
        //         bat "docker run --name keycloakcontainer -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:legacy"
                
        //     } 
        // }
        
        
    }   
}


```





```


pipeline {
    agent any

    stages {
        
        stage('Code ') {
            steps {
              
              echo "Cloning from github"
              git url:'https://github.com/sagar-iitg/Jenkins-Project-Node.git', branch:'master'
                
                
            }
        }
        stage('Build'){
             steps {
            echo "Building docker image"
              
            sh 'docker build . -t sagarkumar99/node-todo-jenkins:latest'
                
            }
            
        }
        stage('Push')
        {
           
            steps{
                echo "Push docker image in docker hub"
                 withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
        sh "docker login -u $USERNAME -p $PASSWORD"
        sh "docker push sagarkumar99/node-todo-jenkins:latest"
    }
            }
        }
        stage('Test'){
             steps {
              
            echo "Testing the new build..."
                
                
            }
            
            
        }
         stage('Check Current Working Directory'){
             steps {
              
                   
                   
                   sh "pwd"
                
            }
         }
          
        stage('Deploy'){
             steps {
              
                   
                   
                   sh "docker-compose down && docker-compose up -d"
                
            }
         
            
        }
        
    }
}


```
