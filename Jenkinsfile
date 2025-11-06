 @Library("shared") _
pipeline {
    agent any

    stages {
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('clone') {
            steps {
                script {
              clone  ("https://github.com/rohankolhapure/django-notes-app.git", "main")
                }
            }
        }
        stage('build') {
            steps{
                 script {
                docker_build ("notes-app", "latest","rohankolhapure")
                 }
            }
        }
        stage('Push to docker hub') {
            steps{
                echo "this is pushing the docker image to docker hub"
                
               script {
                   docker_push ("notes-app","latest","rohankolhapure")
                }
                echo "docker imgae pushing successful"
            }
        }
        stage('Deploy') {
            steps{
                echo "this deploying the code"
                sh "docker run -d -p 8000:8000 notes-app:latest"

             echo "Code has benn run successfully"
            }
        }
    }
}
