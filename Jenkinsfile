pipeline {
    agent any
	tools{
	    
	    maven 'localMAVEN'
	    jdk 'localJDK'
	}

    stages {
        stage('Build') {
            steps {
               
                bat 'mvn clean package'
                 echo 'Building..'
            }
            post{
                
                success{
                    
                    echo 'now archiving..'
                    archiveArtifacts artifacts:'**/target/*.war'
                }

            }
           }
            stage('deploy to staging'){
                              
                              steps{
                                  build job:'PAC_deploy-to-staging'
                                  
                              }

                          }
        
       
    }
}