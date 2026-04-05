
@Library("Shared") _
pipeline {
    agent { label "node" }

    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
               script{
                clone("https://github.com/shwetabhore18/django-notes-app.git", "main")
               }
            }
        }

        stage("Build") {
            steps {
               script{
                   docker_build("notes", "latest", "shweta01818")
               }
                
            }
        }

        stage("Test") {
            steps {
                echo "this is testing the code"
            }
        }
        stage("push to dockerhub"){
            steps{
                script{
                    docker_push("notes", "latest", "shweta01818")
                }
                }
        }

        stage("Deploy") {
            steps {
                echo "this is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
