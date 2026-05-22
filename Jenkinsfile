pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = 'AKIASAKCHINAQJGF54PK'
        AWS_SECRET_ACCESS_KEY = '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'
        AWS_DEFAULT_REGION    = 'us-west-2'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/prashantmukadam16/3-tier-architecture.git'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }
}
