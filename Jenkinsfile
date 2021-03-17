pipeline {

	agent any

	stages {
	
		stage('Build') {
		
			steps {
				sh "./gradlew build"
			}
		}
		
		stage('Test') {
		
			steps {
				sh "./gradlew test"
			}
		
			post {
				success {
					junit '**/build/test-results/test/*.xml'
					archiveArtifacts 'target/*.jar'
				}
			}
		}
	}
}