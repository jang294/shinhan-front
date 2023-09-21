pipeline {
    agent any

    stages {
        stage('parallel stages') {
            parallel {
                stage('prepare') {
                    steps {
                        echo 'prepare'
                        git branch: "${BRANCH}", credentialsId: "GIT_ACCOUNT", url: 'https://github.com/jang294/shinhan-front.git'
                        sh 'ls -al'
                    }
                }
                stage('build') {
                    steps {
                        sh 'ls -al'
                        sh "yarn install"
                        sh "CI=false yarn build"
                    }
                }
                stage('deploy') {
                    steps {
                        sh "ls -al"
                        echo 'deploy'
                    }
                }
            }
        }
    }
}
