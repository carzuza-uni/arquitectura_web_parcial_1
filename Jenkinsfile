pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/carzuza-uni/arquitectura_web_parcial_1.git'
            }
        }
        stage('Init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Plan') {
            steps {
                sh 'terraform plan'
            }
        }
        stage('Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }
    post {
        success {
            slackSend (color: '#00FF00', message: "Deployment successful: ${env.JOB_NAME} [${env.BUILD_NUMBER}]")
        }
        failure {
            slackSend (color: '#FF0000', message: "Deployment failed: ${env.JOB_NAME} [${env.BUILD_NUMBER}]")
        }
    }
}
