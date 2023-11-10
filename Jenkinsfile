pipeline {
    agent {
        node {
            label "linux"
        }
    }

    stages {
        stage('Build'){
           steps {
            echo "Build"
           }
        }

        stage('Test'){
           steps {
            echo "Test"
           }
        }

        stage('Deploy'){
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