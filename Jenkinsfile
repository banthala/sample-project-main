pipeline {
    agent any
    
    tools {
        maven 'My_Maven'
    }
    

    stages{
       stage('Build'){
          steps {
               sh 'mvn clean package'
          }
          post {
               success {
                   echo 'Archiving the artifacts'
                   archiveArtifacts artifacts: '**/target/*.war'
               }
          }
       }
       stage ('Deploy to tomcat server'){
         steps{
               deploy adapters: [tomcat9(credentialsId: '90927b6b-514b-4644-8ad0-9e40d9533462', path: '', url: 'http://23.20.25.157:8081')], contextPath: null, war: '**/*.war'  

      
         }  
       }
     }    
}
