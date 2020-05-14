pipeline {
		agent any
		//agent { docker {image 'maven:3.6.3'}}
		//agent { docker {image 'node:13.8'}}

		environment {
			dockerHome = tool 'MyDocker'
			mavenHome = tool'MyMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages {
			stage('checkout') {
				steps {
					echo "mvn --version"
					sh 'mvn --version'
					echo "docker version"
					sh 'docker version'
					//echo "node --version"
					//sh 'node --version'
					echo "Build"
					echo "PATH - $PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
					echo "BUILD_TAG - $env.BUILD_TAG"
					echo "BUILD_URL - $env.BUILD_URL"
				}
			}
			stage('Compile') {
				steps {
					echo "compile"
					sh 'mvn clean compile'
				}
			}
			stage('Test') {
				steps {
					echo "Test"
					sh 'mvn test'
				}
			}
			stage('Integration Test') {
				steps {
					echo "Integration Test"
					sh 'mvn failsafe:integration-test failsafe:verify'
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