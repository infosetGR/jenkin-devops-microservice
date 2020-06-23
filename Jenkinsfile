//SCRIPTED

//DECLARATIVE 
pipeline {
	agent any
	environment {
		mavenHome = tool 'myMaven' 
		//dockerHome= tool 'myDocker'
		//PATH="$mavenHome/bin:$dockerHome/bin:PATH"
		PATH="$mavenHome/bin:$PATH"
	}
	//agent { docker { image 'maven:3.6.3'}}
	//agent { docker { image 'node:13.8'}}
	stages {
		stage('Checkout') {
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
		stage('Build') {
			steps {
				echo "Build"
				sh "mvn clean compile"
			}

		}
		stage('Test') {
			steps {
				echo "Test"
				sh "mvn test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package') {
			steps {
				echo "Package"
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image') {
			steps {
				// "docker build -t fotisss/currency-exchange-devops:$env.BUILD_TAG"
				script {
					docker.build("fotisss/currency-exchange-devops:$env.BUILD_TAG")
				}

			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('','dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}

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
