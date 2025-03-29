@Library("Shared") _

pipeline {
    agent { label "abs" }

    stages {
        
        stage('Hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                script{
                    clone("https://github.com/Harsh07102003/django-notes-app.git","main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    docker_build("notes-app","latest","harsh07102003")
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                script{
                    docker_push("notes-app","latest","harsh07102003")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "This is Deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
