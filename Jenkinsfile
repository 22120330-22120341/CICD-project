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
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'Thai668084', usernameVariable: '22120330')]) {
                    echo "${22120330}" | docker login -u "${Thai668084}" --password-stdin
                    sh 'docker image push 22120330/cicd-project:v$BUILD_ID'
                    sh 'docker image push 22120330/cicd-project:lastest'
                }
            }
        }

    }
}