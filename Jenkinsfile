pipeline {
		agent any
		stages {
			stage('Build') {
				steps {
					echo "Build"
				}
			}
			stage('Test') {
				steps {
					echo "Test"
				}
			}
			stage('Integration Test') {
				steps {
					echo "Integration Test"
				}
			}
		} 
		post {
			always {
				echo 'I always runs.'
			}
			success {
				echo 'I run if build completes successfully.'
			}
			failure {
				echo 'I run if build is failed'
			}
		}
}