//SCRIPTED
// node {	
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// }

//DECLARATIVE
pipeline {
		//agent any
		agent {
			docker {
				image 'maven:3.6.3'
			}
		}
		stages {
			stage('Build') {
				steps {
					sh 'mvn --version' //sh-shell script is used to print the actual value.
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
