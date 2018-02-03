pipeline {
    agent any

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
        
       
    }
}