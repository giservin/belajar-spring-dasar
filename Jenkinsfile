@Library("belajar-jenkins-shared-library@main") _

import giservintz.jenkins.Output;

pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage("Hello World") {
            steps {
                script {
                    hello("Abirafdi")
                    // memanggil file groovy (sesuai nama nya) di vars shared library , menggunakan fungsi nya 
                    hello.hello_world()
                    // memanggil class 
                    Output.hello(this, "Giservin Tifira Zain")
                }
            }
        }
    }
}
