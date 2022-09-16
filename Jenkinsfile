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
        stage("Deploy docker image") {
            steps {
                sshagent(credentials: ['krzys-remote-app']) {
                      sh '''
                        ls -l
                      '''
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