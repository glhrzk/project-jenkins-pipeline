pipeline {
    agent {
        node {
            label "linux"
        }
    }

    stages {
        stage('Build'){
           steps {

            script {
                for (int i = 0; i < 10; i++){
                    echo("script ${i}")
                }
            }

            echo("Start Build")
            sh("chmod 777 mvnw")
            sh("./mvnw clean compile test-compile")
            echo("Finish Build")
           }
        }

        stage('Test'){
           steps {
            echo("Start Test")
            sh("./mvnw test")
            echo("Finish Test")
           }
        }

        stage('Deploy'){
           steps {
            echo("Deploy 1")
            sleep(5)
            echo("Deploy 2")
            echo("Deploy 3")
           }
        }
    }

    post {
        always {
            echo "I will always say Hello!"
        }

        success {
            echo "Yay, Build Success"
        }

        failure {
            echo "Oh no, Build Failure"
        }

        cleanup {
            echo "Its time to cleanup!"
        }

    }
}