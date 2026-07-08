pipeline {
	agent any

	environment{
		APP_NAME = "Grocery Website"
		VERSION = "1.0"
	}

	stages{
		stage('Environment') {
			steps{
				sh 'echo "Application Name: $APP_NAME" '
				sh 'echo "Version: $VERSION" '
			}
		}

		stage('workspace') {
			steps{
				sh 'pwd'
				sh 'ls -la'
			}
		}	

	}
}
