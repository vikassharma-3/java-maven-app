pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("build jar") {
            steps {
                echo "building the application"
                sh 'mvn package'
            }
        }
        stage("build images") {
            steps {
                echo "building the images"
                withCredentials([usernamePassword(credentialsId: 'Docker hub repo', passwordVariable: 'PASS', usernameVariable: 'USER')]){
                    sh 'docker build -t psychovik/demo-app:jma-2.0 .'
                    sh "echo $PASS | docker login -u $USER --password-stdin"
                    sh 'docker push psychovik/demo-app:jma-2.0'
                }
            }
        }
        stage("deploy") {
            steps {
                echo "deploy the application"
            }
        }
    }
}