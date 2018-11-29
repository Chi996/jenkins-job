pipeline {
    agent any

    stages {
        stage('Checkout Project2.') {
            steps {
                script {
                    if (params.PROMOTE_FROM_ENVIRONMENT != null) {
                        checkout([$class: 'GitSCM',
                        		branches: [[name: params.CHECKOUT_1_GIT_COMMIT]],
                        		userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project2.git']]])
                    }else{
                        checkout([$class: 'GitSCM',
                                 branches: [[name: params.ENVIRONMENT]],
                                 userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project2.git']]])
                    }
                }
            }
        }
        stage('Build Project2') {
             steps {
                 sh 'ls -al'
             }
        }
        stage('Checkout Project3') {
            steps {
                script {
                    if (params.PROMOTE_FROM_ENVIRONMENT != null) {
                        checkout([$class: 'GitSCM',
                                branches: [[name: params.CHECKOUT_2_GIT_COMMIT]],
                                userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project3.git']]])
                    }else{
                        checkout([$class: 'GitSCM',
                                 branches: [[name: params.ENVIRONMENT]],
                                 userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project3.git']]])
                    }
                }
            }
        }
        stage('Build Project3') {
             steps {
                sh 'ls -al'
             }
        }
    }
}