pipeline {
    agent {
        node {
            label "linux && java11"
        }
    }
    stages {
        stage("Build"){
            steps {
                echo("Hello Build")
                sh "error"
            }
        }

        stage("Test"){
            steps {
                echo("Hello Test")
                sh "error"
            }
        }

        stage("Deploy"){
            steps {
                echo("Hello Deploy")
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