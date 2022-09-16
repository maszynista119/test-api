pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
        DOCKERHUB_ACCESS_TOKEN=credentials("dockerhubaccesstoken")
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
                    docker.withRegistry("https://index.docker.io/v1/", "dockerhub") {
                        def customImage = docker.build("maszynista119/testing:${GIT_COMMIT}")

                        customImage.push()
                    }
                }
            }
        }
        stage("Deploy docker image") {
            steps {
                script {
                    def dockerRun = "docker login -u maszynista119 -p ${DOCKERHUB_ACCESS_TOKEN} && docker pull maszynista119/testing:${GIT_COMMIT} && docker run -d -p 8081:80 maszynista119/testing:${GIT_COMMIT} && docker logout"
                    sshagent(credentials: ['krzys-remote-app']) {
                          sh "ssh -o StrictHostKeyChecking=no root@157.230.119.113 ${dockerRun}"

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