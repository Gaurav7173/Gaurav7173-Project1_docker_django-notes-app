@Library("shared") _
pipeline {
    
    agent {
        label "vinod"
    }

    stages {
        stage("Hello")
        {
            steps{
                echo "hello"
                script{
                    hello()
                }
            }
        }
        stage("code") {
            steps {
                script{
                    clone("https://github.com/Gaurav7173/Gaurav7173-Project1_docker_django-notes-app.git","main")
                }
                
            }
        }

        stage("build") {
            steps {
                script{
                    docker_build()
                }
            }
        }

        stage("push to dockerhub") {
            steps {
                script{
                    pushDockerImages('dockerhubcred')
                }
                
            }
        }

        stage("deploy") {
            steps {
                sh 'docker compose down'
                sh 'docker compose up -d'
                echo "Application deployed successfully"
            }
        }
    }
}
