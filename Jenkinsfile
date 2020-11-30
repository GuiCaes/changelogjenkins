pipeline{
	agent any
	environment {
        NAME = "test"
        WORKDIR = pwd()
	}
	stages {
		stage("First Stage") {
            steps{
                echo "Current commit: ${env.GIT_COMMIT} (build ${BUILD_NUMBER})"
                echo "Commit used in last build: ${env.GIT_PREVIOUS_COMMIT}"
                echo "Commit used in last successful build: ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}"
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