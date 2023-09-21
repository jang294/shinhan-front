pipeline {
    agent any
    tools {
        nodejs "node 16"
        git "git"
    }
    stages {
        stage('prepare') {
            steps {
                echo 'prepare'
                 git branch: "${BRANCH}", credentialsId: "GIT_ACCOUNT", url: 'https://github.com/jang294/shinhan-front.git'
                 sh  'ls -al'
            }
        }
        stage('build') {
            steps {
                        sh 'ls -al'
                        sh "npm install"
                        sh "CI=false npm build"
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
