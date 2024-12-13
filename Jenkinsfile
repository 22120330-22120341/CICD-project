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
                sh 'docker image build -t 22120330/cicd-project:v$BUILD_ID .'
                sh 'docker image tag 22120330/cicd-project:v$BUILD_ID 22120330/cicd-project:lastest'
            }
        }
        stage("Image push"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: '123', usernameVariable: '22120330')]) {
                    sh "docker login -u ${22120330} -p ${123}"
                    sh 'docker image push 22120330/cicd-project:v$BUILD_ID'
                    sh 'docker image push 22120330/cicd-project:lastest'
                }
            }
        }

    }
}