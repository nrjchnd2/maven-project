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
             stage('deploy to production'){
                 
                 steps{
                     
                     timeout(time:5,unit:'DAYS'){
                         input message:'Approve Production Deployement ?'
                     }
                     build job:'PAC_deploy-to-production'
                     }
                     post{
                         success{
                             echo "deployed to production"
                             
                         }
                         failure{
                             
                             echo "deployment to Production Failed !"
                         }


                         
                     }


                 

             }

        
       
    }
}