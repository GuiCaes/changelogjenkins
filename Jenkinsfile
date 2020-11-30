pipeline{
	agent any
	environment {
        	NAME = "test"
        	WORKDIR = pwd()
	}
	stages {
		stage("First Stage") {
            		echo "hey"
		}
        }
    }
    post {
        failure {
            echo "fail"
        }
        success {
            echo "success"
        }
    }
}
