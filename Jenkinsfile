pipeline {

agent any

    tools{
        maven 'mymaven'
        jdk 'myjava'
    }

stages {

stage('Checkout the code'){
           steps{
             git url: 'https://github.com/PMayukh/devops_june2021.git', branch: 'master'
           }
}

      stage('Build test and Package '){
      
           steps{
               sh """
               mvn package
               """
           }
       }

stage('Run the spring maven app'){
steps {
           
	sh """
	mvn spring-boot:run
	"""
   }
  }   

 }

post {

          always{
              echo "Job Completed"
          }
      }   

}
