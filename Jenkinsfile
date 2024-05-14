//SCRIPTED
//DECLARATIVE
pipeline {
	agent any
	stages {
		stage('build'){
			steps{
				echo "Build"
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
