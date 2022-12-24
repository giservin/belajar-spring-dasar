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
                echo "Build"
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
