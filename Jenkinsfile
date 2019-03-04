pipeline {
  agent any
  tools {
   maven 'maven3.6.0'
   jdk 'java1.8.0'
 }
 stages {
  stage('Build') {
  steps {
    sh "mvn -B -DskipTests clean package"
    }
    }
 

   stage ('Deploy') {
  steps {
    sh 'java -jar single-module/target/single-module-project.jar'
    }
    }

   
    
     stage('Test') {
            steps {
                sh 'mvn test'
            }
     }
       stage('Upload'){
         steps {
           
            sh 'curl -X PUT -u admin:5r5h7sb5w -T single-module/target/single-module-project.jar "http://13.71.125.61:8081/artifactory/example-repo-local/single-module-project.jar"'
         }
       }
        
 }
}
