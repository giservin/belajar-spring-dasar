@Library("belajar-jenkins-shared-library@main") _

pipeline {
    agent any
    stages {
        stage("Hello World") {
            steps {
                script {
                    // memanggil file groovy (sesuai nama nya) di vars shared library , menggunakan fungsi nya 
                    hello.hello_world()
                }
            }
        }
    }
}
