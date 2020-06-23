//SCRIPTED

//DECLARATIVE 
pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	} post {
		always {
			echo 'Iam awesome'
		}
		success {
			echo 'I run success'
		}
		failure {
			echo 'I run failure'
		}

	}
	
}
