//SCRIPTED
//DECLARATIVE
pipeline {
	// agent {
	// 	docker{
	// 		image 'maven:3.9.6'
	// 	}
	// }
	agent any
	environment{
		dockerHome= tool 'MavenDocker'
		mavenHome= tool 'JenkinMaven'
		PATH="$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "Build" 
				echo "$PATH"
				echo "Build BumNumber -$env.BUILD_NUMBER"
				echo "$env.BUILD_ID"
				echo "$env.JOB_NAME"
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		// stage('Test'){
		// 	steps{
		// 		sh "mvn test"
		// 	}
		// }
		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image'){
			steps{
				//"docker build -t gauravraj/currency-exchange-devops:$env.BUILD_TAG"
				script{
					dockerImage = docker.build("gauravraj/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('','dockerhub'){
					dockerImage.push();
					dockerImage.push('latest')
					}
				}
			}
		}
	}
	post {
		always {
			echo "FINSHED!!"
		}
		success {
			echo "SUCCESS!!"
		}
		failure {
			echo "FAILURE!!"
		}
	}
}
