pipeline {

	agent any
	
	stages {
		stage('Build') {
		
			steps {
				sh "gradle build"
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