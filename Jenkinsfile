pipeline {

	agent any
	node {
    	checkout scm 
    }
	
	stages {
		stage('Build') {
		
			steps {
				sh "./gradlew build"
			}
			
			post {
				success {
					junit '**/target/surefire-reports/TEST-*.xml'
					archiveArtifacts 'target/*.jar'
				}
			}
		}
	}
}