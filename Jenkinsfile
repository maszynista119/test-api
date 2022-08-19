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
                docker.withRegistry("https://hub.docker.com/repository/docker/maszynista119/testing", "dockerhub") {
                    def customeImage = docker.build("testapi");
                    customeImage.push();
                }
            }
        }
    }
}