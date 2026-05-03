pipeline {
    // these are prerequisites
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        COURSE = "Jenkins AWS"
        appVersion = ""
    }
    options {
        timeout(time : 10, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
// this is build sction
    stages {
        stage('Read Version') {
            steps {
                script{
                    def packageJSON = readJSON file: 'package.json'
                    appVersion = packageJSON.version
                    echo "app version: ${appVersion}"
                }
            }
        }
        stage('Install Dependencies'){
            steps {
                script{
                    sh """
                        npm install
                   """
                }
            }
        }
        stage('Deploy') {
            steps {
                script{
                    sh """
                        echo "Deploying"
                    """
                }
            }
        }
    }
    post {
         always{
            echo "I will always say Hello again!"
            cleanWs()
         }
         success {
            echo 'I will run if success'
         }
         failure {
            echo 'I will run if failure'
         }
         aborted {
            echo 'pipeline is aborted'
         }
    }
}