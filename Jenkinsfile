pipeline {
    agent {
        node {
            label "linux"
        }
    }

    stages {
        stage('Build'){
           steps {
            echo("Start Build")
            sh("./mvnw clean compile test-compile")
            echo("Finish Build")
           }
        }

        stage('Test'){
           steps {
            echo("Start Test")
            sh(".mvnw test")
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