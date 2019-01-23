pipeline {
    agent any

    stages {
        stage('Checkout Project2.') {
            steps {
                script {
                    if (params.PROMOTE_FROM_ENVIRONMENT != null) {
                        checkout([$class: 'GitSCM', doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [],
                        		branches: [[name: params.PROJECT2_GIT_COMMIT]],
                        		userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project2.git', name:'project2']]])
                    }else{
                        checkout([$class: 'GitSCM', doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [],
                                 branches: [[name: params.ENVIRONMENT]],
                                 userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project2.git', name:'project2']]])
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
                                doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', noTags: true, reference: '', shallow: true], [$class: 'RelativeTargetDirectory', relativeTargetDir: 'project3']], submoduleCfg: [],
                                branches: [[name: params.PROJECT3_GIT_COMMIT]],
                                userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project3.git', name:'project3']]])
                    }else{
                        checkout([$class: 'GitSCM',
                                 doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', noTags: true, reference: '', shallow: true], [$class: 'RelativeTargetDirectory', relativeTargetDir: 'project3']], submoduleCfg: [],
                                 branches: [[name: params.ENVIRONMENT]],
                                 userRemoteConfigs: [[url: 'https://github.com/Chi996/jenkins-test-project3.git', name:'project3']]])
                    }
                }
            }
        }
        stage('Build Project3') {
             steps {
                sh 'ls -al'
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