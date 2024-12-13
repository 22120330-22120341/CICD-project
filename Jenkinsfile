pipeline{
    agent any
    environment {
        USERNAME = '22120330' // Thay tên đăng nhập
        PASSWORD = 'Thai668084' // Thay mật khẩu
    }
    stages{
        stage("Code checkout"){
            steps{
                git branch: 'main', credentialsId: 'docker-hub', url: 'https://github.com/22120330-22120341/CICD-project.git'
            }
        }
        stage("Image build"){
            steps{
                sh 'docker image build -t 22120330/cicd-project:v$BUILD_ID .'
                sh 'docker image tag 22120330/cicd-project:v$BUILD_ID 22120330/cicd-project:latest'
            }
        }
        stage("Image push"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'Thai668084', usernameVariable: '22120330')]) {
                    sh """
                echo $PASSWORD | docker login -u $USERNAME --password-stdin
                """
                    sh 'docker image push 22120330/cicd-project:v$BUILD_ID'
                    sh 'docker image push 22120330/cicd-project:latest'
                }
            }
        }
        stage("Container creating"){
            steps{
                sh 'docker run -itd --name cicd-project -p 3000:3000 22120330/cicd-project:latest'
            }
        }

    }
}