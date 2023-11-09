def gv

pipeline {
    agent any

    parameters{
        choice(name: 'Version', choices: ['1.1.0','1.1.1','1.1.2'], description: 'Select Version')
        booleanParam(name: 'executeTest',defaultValue: true, description: '')
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    echo "building jar"
                    //gv.buildJar()
                }
            }
        }
        stage("Test image") {
            when {
                expression{
                    params.executeTest
                }
            }
            steps {
                script {
                    echo "building image"
                    //gv.buildImage()
                }
            }
        }        
        stage("build image") {
            steps {
                script {
                    echo "building image"
                    //gv.buildImage()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    echo "deploying"
                    //gv.deployApp()
                }
            }
        }
    }   
}