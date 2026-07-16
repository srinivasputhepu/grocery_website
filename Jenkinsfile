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
                echo "Environment: ${params.ENVIRONMENT}"

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

        stage('Credentials Demo') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: "test-login",
                        usernameVariable: 'USERNAME',
                        passwordVariable: 'PASSWORD'
                        )
                 ])

                {

                 sh 'echo $USERNAME'
                 sh 'echo $PASSWORD'
                }
                sh 'echo "Outside block: $USERNAME" '

            }
        }

        stage('Build Docker Image') {
            steps { sh 'docker build -t grocery-test:v1 .' }
            }

        stage('Deployment') {
            steps {
                sh '''
                    docker run -d --name grocery-test -p 8081:80 grocery-test:v1
                '''
                }
        }
	}
}
