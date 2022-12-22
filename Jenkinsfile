pipeline {
    agent any 

    stages {
        stage('Hello') {
            steps {
                echo "hello world"
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
