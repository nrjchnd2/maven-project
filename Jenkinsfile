pipeline {
    agent any
    tools{
        
        maven 'localMAVEN'
        jdk 'localJDK'
    }
  
    parameters {
         string(name: 'tomcat_dev', defaultValue: '18.218.210.140', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '18.220.180.153', description: 'Production Server')
    }
    

    
   
    stages{
        
        stage('build'){
            steps{
                
                bat 'mvn clean package'
            }
            post{
                
                success{
                    echo 'Now archiving'
                    archiveArtifacts artifacts:'**/target/*.war'
                }

            }


            
        }
        
        stage('deployement'){
         	steps{
                	    bat "echo y|pscp.exe -i D:\\AWS\\mykey.ppk \\webapp\\target\\webapp.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat8/webapps"
                	}

                    
                    
                }
                   
                }

            

        }


    

    

   
