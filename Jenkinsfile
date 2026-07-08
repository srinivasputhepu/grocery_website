pipeline {
    agent any

        stages {

            stage('Checkout') {
                steps {
                    echo 'Repository checked out successfully.' 
                    }
            }
    
            stage('List files') {
                steps {
                    sh 'pwd'
                    sh 'ls -la'
                      }
            }

            stage('Display Home Page') {
                steps {
                    sh 'cat index.html'                    
                    }                
                }
            }
        }
