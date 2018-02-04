pipeline {
    agent any
    tools{
        
        maven 'localMAVEN'
        jdk 'localJDK'
    }
    parameters{
        
        string(name:'tomcat-dev',defaultValue:'18.218.210.140',description:'staging server')
        string(name:'tomcat-prd',defaultValue:'18.220.180.153',description:'production server')
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
            
            parallel{
                
                stage('deploy to staging'){
                	steps{
                	    bat 'pscp -scp -i C:\\Program Files (x86)\\Jenkins\\tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat-dev}:/var/lib/tomcat8/webapps'
                	}

                    
                    
                }
                 stage('deploy to production'){
                	steps{
                	    bat 'pscp -scp -i C:\\Program Files (x86)\\Jenkins\\tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat-prd}:/var/lib/tomcat8/webapps'
                	}

                    
                    
                }

            }

        }


    }



}