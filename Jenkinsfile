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
                	    bat "scp -i D:\\AWS\\mykey.ppk C:\\Program Files (x86)\\Jenkins\\workspace\\Fully-Automated\\webapp\\target\\*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat8/webapps"
                	}

                    
                    
                }
                   
                }

            

        }


    

    

   
