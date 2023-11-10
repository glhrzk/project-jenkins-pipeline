pipeline {
    agent {
        node {
            label "linux"
        }
    }

    stages {
        stages('Build'){
           steps {
            echo "Build"
           }
        }

        stages('Test'){
           steps {
            echo "Test"
           }
        }

        stages('Deploy'){
           steps {
            echo "Deploy"
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