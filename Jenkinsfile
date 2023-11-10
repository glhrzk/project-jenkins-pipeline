pipeline {
    agent {
        node {
            label "linux"
        }
    }

    stages {
        stage('Build'){
           steps {
            echo("Build 1")
            echo("Build 2")
            sleep(5)
            echo("Build 3")
           }
        }

        stage('Test'){
           steps {
            echo("Test 1")
            echo("Test 2")
            sleep(5)
            echo("Test 3")
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