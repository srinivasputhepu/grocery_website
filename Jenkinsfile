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
				echo "Version: ${params.VERSION}"
                echo "Environment: ${params.ENVIRONMENT"}

                sh """
                    echo "Version from Shell: ${params.VERSION}"
                    echo "Environment from Shell: ${params.ENVIRONMENT}"
                """
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
