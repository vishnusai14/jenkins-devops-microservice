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
		stage("Build Docker Images") {
			steps {
				script {
					dockerImage = docker.build("vishnuprasanna/currency-exchange-devops:+${env.BUILD_TAG}")
				}
			}
		}
		stage("Push Docker Image") {
			steps {
				script {
					docker.withRegistry("", DOCKER_CREDENTIALS_ID) {
						dockerImage.push(env.BUILD_TAG)
						dockerImage.push("latest")
					}
				}
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