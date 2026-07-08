pipeline {
	agent any

        parameters {
            string (
                name: 'VERSION',
                defaultValue: '2.0',
                description: 'Application Version'
            )

            choice(
                name: 'ENVIRONMENT',
                choices: ['Development', 'Testing', 'Production'],
                description: "Select an Environment"
            )
        }

	stages{
		stage('Print Parameters') {
			steps{
				sh 'echo "Version: $VERSION" '
                sh 'echo "Environment: $ENVIRONMENT" '
			}
		}

		stage('Workspace') {
			steps{
				sh 'pwd'
				sh 'ls -la'
			}
		}	

	}
}
