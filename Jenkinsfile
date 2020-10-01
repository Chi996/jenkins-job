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

        stage('Checkout Project3') {
            steps {
                script {
                    if (params.PROMOTE_FROM_ENVIRONMENT != null) {
                        checkout([$class: 'GitSCM',
                                doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', noTags: true, reference: '', shallow: true], [$class: 'RelativeTargetDirectory', relativeTargetDir: 'project3']], submoduleCfg: [],
                                branches: [[name: params.PROJECT3_GIT_COMMIT]],
                                userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project3.git', name:'project3']]])
                    }else{
                        checkout([$class: 'GitSCM',
                                 doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', noTags: true, reference: '', shallow: true], [$class: 'RelativeTargetDirectory', relativeTargetDir: 'project3']], submoduleCfg: [],
                                 branches: [[name: "master"]],
                                 userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project3.git', name:'project3']]])
                    }
                }
            }
        }

        stage('Print params'){
            steps {
                echo "ENVIRONMENT: ${params.ENVIRONMENT}"
                echo "PARAM_GIT_BRANCH: ${params.PARAM_GIT_BRANCH}"
                bash echo "PARAM_GIT_BRANCH: $PARAM_GIT_BRANCH"
                echo "PROMOTE_FROM_ENVIRONMENT: ${params.PROMOTE_FROM_ENVIRONMENT}"
                echo "PROMOTE_FROM_VERSION: ${params.PROMOTE_FROM_VERSION}"

                echo "ROOT_GIT_COMMIT: ${params.ROOT_GIT_COMMIT}"
                echo "PROJECT2_GIT_COMMIT: ${params.PROJECT2_GIT_COMMIT}"
                echo "PROJECT3_GIT_COMMIT: ${params.PROJECT3_GIT_COMMIT}"
            }
        }
    }
}