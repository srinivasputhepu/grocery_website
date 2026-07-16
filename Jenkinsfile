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

        stage('Build Docker Image') {
            steps { sh "docker build -t grocery-website:${env.BUILD_NUMBER} -t grocery-website:latest ." }
            }

        stage('Deployment') {
            steps {
                sh """
                    docker rm -f grocery-test                    
                    docker run -d --name grocery-test -p 8081:80 grocery-website:${env.BUILD_NUMBER}
                    """
                }
        }
	}

    post {
        always { echo 'Pipeline Finished' }
        success { echo 'Pipeline Succeeded' }
        failure { echo 'Pipeline Failed' }       
    }
}
