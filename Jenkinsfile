pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    }
    stages {
        stage("build") {
            steps {
                echo "build"
            }
        }
        stage("test") {
            steps {
                echo "kurwy jebany wypierdalac"
            }
        }
        stage("build docker image") {
            steps {
                script {
                    docker.withRegistry("https://docker.io", "dockerhub") {
                        def customImage = docker.build("maszynista119/testing:${GIT_COMMIT}")

                        customImage.push()
                    }
                }
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}