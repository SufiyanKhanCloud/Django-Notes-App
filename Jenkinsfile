@Library("Shared") _
pipeline{
    
    agent { label "sufi" }
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
                script{
                clone("https://github.com/SufiyanKhanCloud/Django-Notes-App","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","sufiyankhan10") 
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","sufiyankhan10")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            } 
        }
    }
}
