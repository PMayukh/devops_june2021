pipeline {

agent none

    tools{
        maven 'mymaven'
        jdk 'myjava'
    }

stages {

stage('Checkout the code'){
	agent 'master'  
           steps{
             git url: 'https://github.com/PMayukh/devops_june2021.git', branch: 'master'
           }
}

      stage('Build test and Package '){
	      agent { 
                label 'Node01'
            }
      
           steps{
               sh """
               mvn package
               """
           }
       }

stage('Run the spring maven app'){
	agent { 
                label 'Node02'
            }
steps {
           
	sh """
	mvn spring-boot:run
	"""
   }
  }   

 }

post {

	success{
	junit '**/target/surefire-reports/*.xml'
	}
	
	always{
              echo "Job Completed"
          }
      }   

}
