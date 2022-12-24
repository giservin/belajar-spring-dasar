pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                echo "hello Build"
                sleep(5)
                echo "hello kedua"
            }
        }
        stage('Test') {
            steps {
                echo "hello Test"
                sleep(2)
            }
        }
        stage('Deploy') {
            steps {
                echo "hello Deploy"
            }
        }
    }

    post {
        always {
            echo "Hello again"
        }
        success {
            echo "Success"
        }
        failure {
            echo "failure!"
        }
        cleanup {
            echo "Testes"
        }
    }
}
