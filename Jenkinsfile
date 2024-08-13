pipeline{ 
	//TO use any docker images as a agent 
	// agent{
	// 	docker {
	// 		image '<Image Name>'
	// 	}
	// }

	tools{
		maven "MAVEN"
	}

	environment {
		DOCKER_CRED = 'docker-hub'
	}
	agent any
	stages{
		stage("Compile the code") {
			steps {
				sh "mvn clean compile"
			}
		}
		stage("Test") {
			steps {
				sh "mvn test"
			}
		}
	}

	post{
		always {
			sh "echo Build Completed"
		}
		success {
			sh "echo Build sucess"
		}
		failure {
			sh "echo Build Failure"
		}
	}
}