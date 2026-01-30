@Library("Shared") _
pipeline{
    agent { label 'anju' }
    
    stages{
        
        stage ("Hello") {
            steps {
                script {
                    hii()
                }
            }
            
        }
        stage("Code Clone"){
            steps{
                scipt{
                code_checkout("https://github.com/AnjanaZare/django-notes-app","main")
                }
            }
        }
        stage("Code Build & Test"){
            steps{
               script{
                   docker_build("notes-app","latest","anjanaz")
                   
               }
            }
        }
        stage("Push To DockerHub"){
            steps{
               script{
                   docker_push("notes-app","latest","anjanaz")
                   
               }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d --build"
            }
        }
    }
}
