pipeline {
		//agent any
		//agent { docker {image 'maven:3.6.3'}}
		agent { docker {image 'node:13.8'}}
		stages {
			stage('Build') {
				steps {
					echo "mvn --version"
					//sh 'mvn --version'
					sh 'node --version'
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
			changed {
				echo "I run if build status changed, say from success to failed or vice versa"
			}
		}
}