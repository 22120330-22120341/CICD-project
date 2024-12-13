pipeline{
    agent any

    stages{
        stage("Code checkout"){
            steps{
                git branch: 'main', credentialsId: 'docker-hub', url: 'https://github.com/22120330-22120341/CICD-project.git'
            }
        }
    }
}