pipeline {
    agent none

    environment {
        AUTHOR = "Giservin"
        EMAIL = "giservin20@giservin.com"
        DB_SERVER = "localhost"
    }

    triggers {
        githubWebHook()
    }

    stages {
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
