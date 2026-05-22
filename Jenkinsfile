pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-west-2'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/prashantmukadam16/3-tier-architecture.git'
            }
        }

        stage('Terraform Destroy') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform destroy'
                }
            }
        }

    post {

        success {
            echo 'Terraform Infrastructure deployed successfully!'
        }

        failure {
            echo 'Terraform deployment failed!'
        }
    }
}
