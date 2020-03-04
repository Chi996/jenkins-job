pipeline {
    agent any

    stages {
        stage('Checkout Project2.') {
            steps {
                script {
                    if (params.PROMOTE_FROM_ENVIRONMENT != null) {
                        checkout([$class: 'GitSCM', doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [],
                        		branches: [[name: params.JENKINS_TEST_PROJECT_GIT_COMMIT]],
                        		userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project.git', name:'jenkins-test-project']]])
                    }else{
                        checkout([$class: 'GitSCM', doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [],
                                 branches: [[name: params.ENVIRONMENT]],
                                 userRemoteConfigs: [[url: 'https://github.com/Chi996/k8s-scripts.git', name:'k8s-script']]])
                    }
                }
            }
        }
        stage('Build Project2') {
             steps {
                 sh 'ls'
             }
        }

        stage('Print params'){
            steps {
                echo "ENVIRONMENT: ${params.ENVIRONMENT}"
                echo "PROMOTE_FROM_ENVIRONMENT: ${params.PROMOTE_FROM_ENVIRONMENT}"
                echo "PROMOTE_FROM_VERSION: ${params.PROMOTE_FROM_VERSION}"

                echo "ROOT_GIT_COMMIT: ${params.ROOT_GIT_COMMIT}"
                echo "PROJECT2_GIT_COMMIT: ${params.PROJECT2_GIT_COMMIT}"
                echo "PROJECT3_GIT_COMMIT: ${params.PROJECT3_GIT_COMMIT}"
            }
        }
    }
}