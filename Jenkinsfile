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
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
				sh 'docker push bharathirajatut/nodeapp:latest'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}