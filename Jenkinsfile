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
                    docker.withRegistry("https://registry.hub.docker.com/v1/repositories/maszynista119/testing/tags", "dockerhub") {
                        def customImage = docker.build("testapi:${GIT_COMMIT}")

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