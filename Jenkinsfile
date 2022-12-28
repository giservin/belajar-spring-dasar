pipeline {
    agent none

    environment {
        AUTHOR = "Giservin"
        EMAIL = "giservin20@giservin.com"
        DB_SERVER = "localhost"
    }

    triggers {
        githubPush()
    }
    
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    stages {
        stage("Preparation") {
            failFast true
            matrix {
                axes {
                    axis {
                        name 'OS'
                        values 'windows', 'linux', 'mac'
                    }
                    axis {
                        name 'ARC'
                        values 'x86', 'x64'
                    }
                }
                excludes {
                    exclude {
                        axis {
                            name 'OS'
                            values 'mac'
                        }
                        axis {
                            name 'ARC'
                            values 'x86'
                        }
                    }
                }
                stages {
                    stage("Prepare OS") {
                        agent {
                            node {
                                label "master"
                            }
                        }
                        steps {
                            echo "Prepare ${OS} ${ARC}"
                        }
                    }
                }
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
                echo "Branch Name : ${env.BRANCH_NAME}"
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
                withCredentials([usernamePassword(
                    credentialsId: "username_rahasia", 
                    usernameVariable: "USER", 
                    passwordVariable: "PASSWORD")]) {
                        sh 'echo "Releasing with user $USER and password $PASSWORD" > secret.txt'
                    }
            }
        }
    }
    
}
