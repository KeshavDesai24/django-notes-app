@Library("HelloLib") _
pipeline {
    agent {
        label "keshav"
    }
    
    stages{
        stage(hello){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                clone("https://github.com/LondheShubham153/django-notes-app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("django_app","latest","keshav635")
                }
            }
        }
        stage("Docker Hub"){
            steps{
                script{
                    docker_push("django_app","latest","keshav635")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is the deploying stage"
                sh "docker compose up -d"
                echo "Application deployed successfully...."
            }
        }
    }
}
