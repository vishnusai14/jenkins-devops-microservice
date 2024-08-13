pipeline{ 
	agent any
	stages{
		stage("Build") {
			sh "echo Building"
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