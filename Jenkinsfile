//SCRIPTED
// node {	
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// }

//DECLARATIVE
pipeline {
		agent any
		// agent {
		// 	docker {
		// 		//image 'maven:3.6.3'
		// 		image 'node:13.8'
		// 	}
		// }

		environment {
			dockerHome = tool 'myDocker'
			mavenHome = tool 'myMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}

		stages {
			stage('Checkout') {
				steps {
					sh 'mvn --version' //sh-shell script is used for actual value or do the actual work.
					//sh 'node --version'
					sh 'docker version'
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
					sh "mvn clean compile"
				}
			}

			stage('Test') {
				steps {
					sh "mvn test"
					echo "Test"
				}
			}
			
			stage('Integration Test') {
				steps {
					sh "mvn failsafe:integration-test failsafe:verify"
					echo "Integration Test"
				}

			}
		} 
		
		post {
			always {
				echo 'I am awesome, I run always'			
			}
			success {
				echo 'I run when you are successful'			
			}
			failure {
				echo 'I run when you fail'			
			}
		}
}
