pipeline {
    agent any
	tools{
	    
	    maven 'localMAVEN'
	    jdk 'localJDK'
	}

    stages {
        stage('Build') {
            steps {
                echo "${JAVA_HOME}"
				echo "${M2_HOME}"
                bat 'mvn clean package'
                 echo 'Building..'
            }
           

        }
        
       
    }
}