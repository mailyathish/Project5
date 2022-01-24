pipeline {
    agent any
	
	  tools
    {
       maven "Maven"
    }

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/mailyathish/Project5.git'
             
          }
        }

stage('JUnit Test') {
   steps {
      
         sh 'mvn clean test' 
      
   }
 }

stage('Integration Test ') {
   steps {
      
         sh 'mvn integration-test' 
      
   }
 }

 stage('Performance Test') {
      steps {
         sh 'mvn -X verify'
      
   }
 }

  stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }

 stage('Docker Build and Tag') {
           steps {
              
               
                sh 'docker build -t rajuyathi/calculator:latest .' 
                
               
          }
        }

   
   /*
   stage('Push Docker Image'){
	steps {
	
	withCredentials([string(credentialsId: 'DockerPWDS', variable: 'DockerPass')]) {
    	// some block

	sh 'docker login -u rajuyathi -p ${DockerPass}'

	
	 // some block
	sh 'docker push rajuyathi/calculator:latest'
	}
   }
   */
	}

	}




/*
node {
   def mvnHome = tool 'M3'

   stage('Checkout Code') { 
      git 'https://github.com/maping/java-maven-calculator-web-app.git'
   }
   stage('JUnit Test') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' clean test"
      } else {
         bat(/"${mvnHome}\bin\mvn" clean test/)
      }
   }
   stage('Integration Test') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' integration-test"
      } else {
         bat(/"${mvnHome}\bin\mvn" integration-test/)
      }
   }
 /*
   stage('Performance Test') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' cargo:start verify cargo:stop"
      } else {
         bat(/"${mvnHome}\bin\mvn" cargo:start verify cargo:stop/)
      }
   }
  
  stage('Performance Test') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' verify"
      } else {
         bat(/"${mvnHome}\bin\mvn" verify/)
      }
   }
   stage('Deploy') {
      timeout(time: 10, unit: 'MINUTES') {
           input message: 'Deploy this web app to production ?'
      }
      echo 'Deploy...'
   }
}
   */
