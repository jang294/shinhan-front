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
                        // 캐시를 활용하여 패키지 다운로드 시간 단축
                        script {
                            def yarnCacheDir = '.yarn-cache'
                            sh "yarn config set cache-folder ${yarnCacheDir}"
                            sh "yarn install" // 캐시를 사용하도록 설정된 디렉토리에 패키지 설치
                        }
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
