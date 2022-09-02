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
				sh 'docker build -t testapi .'
                sh 'echo Zapalnik1! | docker login -u maszynista119 --password-stdin'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}