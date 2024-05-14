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
		stage('build'){
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
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
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
