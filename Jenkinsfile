pipeline {
    agent {
        node {
            label "linux && java11"
        }
    }
    stages {
        stage("Build"){
            steps {

            script {
                for (int i = 0; i < 10; i++){
                    echo("Script ${i}")
                }
            }

            echo("start Build")
            sh("chmod +x mvnw")
            sh("./mvnw clean compile test-compile")
            echo("finish Build")
            }
        }

        stage("Test"){
            steps {
                echo("start test")
                echo("./mvnw test")
                echo("finish test")
            }
        }

        stage("Deploy"){
            steps {
                echo "Hello Deploy 1"
                echo "Hello Deploy 2"
                echo "Hello Deploy 3"
            }
        }
    }

    post {
        always {
            echo 'I will always say Hello again!'
        }

        success {
            echo "Yay, success!"
        }

        failure {
            echo "Oh no, failure!"
        }

        cleanup {
            echo "Don't core success or error"
        }

    }
}