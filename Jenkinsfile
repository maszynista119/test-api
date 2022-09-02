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
				sh 'docker build -t testapi:${GIT_COMMIT} .'
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh "docker tag testapi:${GIT_COMMIT} maszynista119/testing:${GIT_COMMIT}"
                sh "docker push testapi:${GIT_COMMIT}"
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}