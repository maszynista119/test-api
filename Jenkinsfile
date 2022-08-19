pipeline {
    agent any
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
                    docker.withRegistry("maszynista119/testing", "dockerhub") {
                        def customeImage = docker.build("testapi:${env.BUILD_ID}");
                        customeImage.push();
                    }
                }
            }
        }
    }
}