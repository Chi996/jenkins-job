pipeline {
    agent any

	environment {
		ENVIRONMENT = "PROD"
	}
	
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the main repository'
				checkout([$class: 'GitSCM', 
						  branches: [[name: '*/master']],
					 userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project2.git']]])
					 
				checkout([$class: 'GitSCM', 
						  branches: [[name: '*/master']],
					 userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project3.git']]])
					 
				echo "ENVIRONMENT: ${params.ENVIRONMENT}"
				echo "PROMOTE_FROM_ENVIRONMENT: ${params.PROMOTE_FROM_ENVIRONMENT}"
				echo "PROMOTE_FROM_VERSION: ${params.PROMOTE_FROM_VERSION}"
				
				echo "CEHCKOUT_0_GIT_COMMIT: ${CEHCKOUT_0_GIT_COMMIT}"
				echo "CEHCKOUT_1_GIT_COMMIT: ${CEHCKOUT_1_GIT_COMMIT}"
				echo "CEHCKOUT_2_GIT_COMMIT: ${CEHCKOUT_2_GIT_COMMIT}"
            }
        }
        stage('Finished') {
            steps {
                echo 'finished'
            }
        }
    }
}