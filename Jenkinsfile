pipeline {
	// Assign to docker slave(s) label, could also be 'any'
    agent {
     label 'docker' 
    }
	
    environment {
        CI = 'true'
    }
	
    stages {
        stage('Build') {
			agent {
				docker {
				  // Set both label and image
				  label 'dockerserver'
				  image 'node:6-alpine'
				  args '-p 3000:3000 -p 5000:5000'
				}
			}
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
			
			agent {
				docker {
				  // Set both label and image
				  label 'dockerserver'
				  image 'node:6-alpine'
				  args '-p 3000:3000 -p 5000:5000'
				}
			}
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}