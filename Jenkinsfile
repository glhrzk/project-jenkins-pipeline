pipeline {
    agent none

    environment {
        AUTHOR = "Galih Rizki"
        EMAIL = "galihrizki23@gmail.com"
    }

    stages {
        stage('Prepare'){
        environment {
            APP = credentials("galih_ganteng")
        }

            agent {
                node {
                    label "linux"
                }
            }

           steps {
            echo("Author: ${AUTHOR}")
            echo("App User: ${APP_USR}")
            echo('App Password: ${APP_PSW}')
            echo("Email: ${EMAIL}")
            echo("Start Job: ${env.JOB_NAME}")
            echo("Start Build: ${env.BUILD_NUMBER}")
            echo("Branch Name: ${env.BRANCH_NAME}")
           }
        }


        stage('Build'){

            agent {
                node {
                    label "linux"
                }
            }

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

            agent {
                node {
                    label "linux"
                }
            }


           steps {

               script {
                def data = [
                    "firstName" : "Galih",
                    "lastName" : "Rizki"
                ]

                writeJSON(file: "data.json", json: data)
               }

            echo("Start Test")
            sh("chmod 777 mvnw")
            sh("./mvnw test")
            echo("Finish Test")
           }
        }

        stage('Deploy'){

            agent {
                node {
                    label "linux"
                }
            }

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