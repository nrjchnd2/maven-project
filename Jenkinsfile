pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                def mvnHome = tool 'M3'
                bat '${mvnHome}/bin/mvn clean package'
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