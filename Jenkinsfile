pipeline{
    agent any

    stages{
        stage("Code checkout"){
            steps{
                git branch: 'main', credentialsId: 'docker-hub', url: 'https://github.com/22120330-22120341/CICD-project.git'
            }
        }
        stage("Image build"){
            steps{
                sh 'docker image build -t 22120330/CICD-project:v$BUILD_ID .'
                sh 'docker image tag 22120330/CICD-project:v$BUILD_ID 22120330/CICD-project:lastest'
            }
        }

    }
}