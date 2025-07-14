@Library("Shared") _
pipeline{
    agent any
    // agent {label "nameofLabel"}
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
                  clone("https://github.com/MohammadRehanPatel/django-notes-app.git","main")
              }
            }
        }
        stage("Build"){
            steps{
            script{
               docker_build("notes-app","latest","mohammadrehanpatel")
            }
                
            }
        }
        stage("Test"){
            steps{
                echo "This is Testing the code"
            }
        }
         stage("Push to Docker Hub"){
            steps{
               script{
                   docker_push("notes-app","latest","mohammadrehanpatel")
               }
                
            }
        }
        stage("Deploy"){
            steps{
                script{
                docker_compose()
                }
            }
        }
    }
}
