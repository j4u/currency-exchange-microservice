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
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
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
