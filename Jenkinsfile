//SCRIPTED

//DECLARATIVE 
pipeline {
	agent any
	environment {
		mavenHome = tool 'myMaven' 
		//dockerHome= tool 'myDocker'
		//PATH="$mavenHome/bin:$dockerHome/bin:PATH"
		PATH="$mavenHome/bin:PATH"
	}
	//agent { docker { image 'maven:3.6.3'}}
	//agent { docker { image 'node:13.8'}}
	stages {
		stage('Build') {
			steps {
				sh "mvn --version"
				sh "docker --version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID- $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
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
	} 
	
	post {
		always {
			echo 'Iam awesome'
		}
		success {
			echo 'I run success'
		}
		failure {
			echo 'I run failure'
		}
		//change

	}
	
}
