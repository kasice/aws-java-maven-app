#!/usr/bin.env groovy

pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application..."

                }
            }
        }
        stage("build") {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    def dockerCmd = 'docker run -d -p 3080:3080 kasice/my-app:latest'
                    sshagent(credentials: ['ec2-server-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@99.79.10.124 ${dockerCmd}"
                   }
                }
            }
        }               
    }
} 
