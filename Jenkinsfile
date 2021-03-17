pipeline {

	agent any

	stages {
	
		stage('Build') {
		
			steps {
				sh "./gradlew clean build"
			}
			
			post {
				success {
					archiveArtifacts '**/build/**/*.jar', fingerprint: true
				}
			}
		}
		
		stage('Test') {
		
			steps {
				sh "./gradlew test"
			}
		
			post {
				success {
					junit '**/build/test-results/test/*.xml'
				}
			}
		}
	}
}