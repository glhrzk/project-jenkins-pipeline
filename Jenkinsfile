pipeline {
    agent none

    environment {
        AUTHOR = "Galih Rizki"
        EMAIL = "galihrizki23@gmail.com"
    }

//     triggers {
//         cron("*/5 * * * *")
//         // pollSCM("*/5 * * * *")
//         // upstream(upstreamProjects: 'job1,job2', treshold: hudson.model.Result.SUCCESS)
//
//     }

    parameters {
        string(name: 'NAME', defaultValue: 'Guest', 'description': 'What is your name?')
        text(name: 'DESCRIPTIONS', defaultValue: '', 'description': 'Tell me about yo')
        booleanParam(name: 'DEPLOY', defaultValue: false, 'description': 'Need to Deploy?')
        choice(name: 'SOCIAL_MEDIA', choices: ['Instagram', 'Facebook', 'Twitter'], 'description': 'Which social media')
        password(name: 'SECRET', defaultValue: 'Guest', 'description': 'Encrypt Key?')
    }

    options {
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'MINUTES')
    }

    stages {
         stage('Parameter'){
            agent {
                node {
                    label "linux"
                }
            }

           steps {
            echo("Hello ${params.NAME}")
            echo("You Descriptions is ${params.DESCRIPTIONS}")
            echo("Your Social media is ${params.SOCIAL_MEDIA}")
            echo("Need to deploy: ${params.DEPLOY} to deploy!")
            echo("Your secret is ${params.SECRET}")
           }
        }


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
            sh('echo "App Password ${APP_PSW}" > "rahasia.txt"')
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
           input {
            message "Can we deploy?"
            ok "Yes, of cource"
            submitter "glhrzk"
            parameters{
                choice(name: "TARGET_ENV", choices: ['DEV', 'QA', 'PROD'], descriptions: "Which Environment?" )
            }
           }


            agent {
                node {
                    label "linux"
                }
            }

           steps {
           echo("Deploy to ${TARGET_ENV}")
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