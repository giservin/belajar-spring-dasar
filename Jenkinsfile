pipeline {
    agent none

    stages {
        stage("Build") {
            agent {
                node {
                    label "master"
                }
            }
            steps {
                echo "Start Job : ${env.JOB_NAME}"
                echo "Start Build : ${env.BUILD_NUMBER}"
                echo "Build Name : ${env.BRANCH_NAME}"
            }
        }
        stage("Deploy") {
            agent {
                node {
                    label "agent-one"
                }
            }
            steps {
                echo "Deploy"
            }
        }
    }
}
