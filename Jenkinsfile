pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                bat 'mvn clean package'
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