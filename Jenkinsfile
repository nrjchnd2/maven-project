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
        
        stage('Test'){
            
            steps{
                echo "trying to connect"
                bat "ssh -i C:\\Program Files (x86)\\Jenkins\\tomcat-demo.pem ec2-user@${params.tomcat_dev}"
            }

        }

    }

   
}