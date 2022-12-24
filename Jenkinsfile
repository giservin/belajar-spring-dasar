pipeline {
    agent{
        node {
            label "agent-one"
        }
    }

    stages {
        stage('Build') {
            steps {
                script {
                    for(int i=0; i<10; i++) {
                        echo "Script ke-${i}"
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    def data = [
                        "firstName": "Eko",
                        "lastName" : "Khannedy"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
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
