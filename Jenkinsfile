pipeline {
    agent none

    environment {
        AUTHOR = "Giservin"
        EMAIL = "giservin20@giservin.com"
        DB_SERVER = "localhost"
    }

    parameters {
        string(name: "NAME", defaultValue: "Guest", description: "What's your name")
        text(name: "DESCRIPTION", defaultValue: "Guest", description: "Describe yourself")
        booleanParam(name: "DEPLOY", defaultValue: false, description: "Deploy gak?")
        choice(name: "SOCIAL_MEDIA", choices: ['Instagram', 'Facebook', 'Twitter'], description: "Which Social Media?")
        password(name: "SECRET", defaultValue: "", description: "Encrypt Key")
    }

    options {
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'SECONDS')
    }

    stages {
        stage("Parameter") {
            agent {
                node {
                    label "master"
                }
            }

            steps {
                echo "HELLO ${params.NAME}!"
                echo "You are ${params.DESCRIPTION}!"
                echo "HELLO ${params.SOCIAL_MEDIA} user!"
                echo "Need to deploy: ${params.DEPLOY}!"
                sh 'echo "this is your password : $params.SECRET"'
            }
        }
        stage("Build") {
            agent {
                node {
                    label "master"
                }
            }
            environment { 
                APP = credentials("username_rahasia")
            }
            steps {
                echo "Start Job : ${env.JOB_NAME}"
                echo "Start Build : ${env.BUILD_NUMBER}"
                echo "Build Name : ${env.BRANCH_NAME}"
                echo "Username : ${APP_USR}"
                // echo "Password : ${APP_PSW}"
                sh 'echo "App Password : $APP_PSW" > password.txt'
            }
        }
        stage("Deploy") {
            agent {
                node {
                    label "agent-one"
                }
            }
            steps {
                echo "Author : ${AUTHOR}"
                echo "Email : ${EMAIL}"
                echo "DB Host : ${DB_SERVER}"
            }
        }
    }
}
