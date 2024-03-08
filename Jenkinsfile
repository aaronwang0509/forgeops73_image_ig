pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS_ID = 'DOCKERHUB_CREDENTIALS_ID'
        IMAGE_NAME = 'aaronwang0509/ig'
        MAJOR_VERSION = '7'
        MINOR_VERSION = '30'
    }
    stages {
        /*
        stage('Build and Push ig Image') {
            steps {
                script {
                    def imageName = "${env.IMAGE_NAME}"
                    def fullVersion = "${env.MAJOR_VERSION}.${env.MINOR_VERSION}.${env.BUILD_NUMBER}"
                    dir('identity-gateway/docker') {
                        docker.build("${imageName}:${fullVersion}")
                        docker.withRegistry('https://index.docker.io/v1/', env.DOCKERHUB_CREDENTIALS_ID) {
                            docker.image("${imageName}:${fullVersion}").push()
                        }
                    }
                }
            }
        }
        */
        stage('Build and Push ig-build Image') {
            steps {
                script {
                    def imageName = "${env.IMAGE_NAME}-build"
                    def fullVersion = "${env.MAJOR_VERSION}.${env.MINOR_VERSION}.${env.BUILD_NUMBER}"
                    dir('ig-build') {
                        docker.build("${imageName}:${fullVersion}")
                        docker.withRegistry('https://index.docker.io/v1/', env.DOCKERHUB_CREDENTIALS_ID) {
                            docker.image("${imageName}:${fullVersion}").push()
                        }
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Build and push completed.'
        }
    }
}