pipeline {

	agent any

	stages {
		stage('Build') {
		
			steps {
				sh "./gradlew build"
			}
			
			post {
				success {
					junit '**/build/test-results/*/.xml'
					archiveArtifacts 'target/*.jar'
				}
			}
		}
	}
}