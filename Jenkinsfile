pipeline {

	agent any

	stages {
	
		stage('Build') {
		
			steps {
				sh "./gradlew clean build"
			}
			
			post {
				success {
					archiveArtifacts artifacts: '**/build/**/*.jar', fingerprint: true
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
		
		stage('Sonarqube') {
            steps {

               sh './gradlew sonarqube  -Dsonar.host.url=http://localhost:9595/ -Dsonar.projectKey=testGradle -Dsonar.login=admin -Dsonar.password=password -Dsonar.junit.reportPaths=./build/test-results/test -Dsonar.binaries=./build/classes'
            }
        }
	}
}