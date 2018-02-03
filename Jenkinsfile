pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                
                bat 'D:\\apache-maven-3.5.2-bin\\apache-maven-3.5.2\\bin\\mvn clean package'
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