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

        stage('Terraform Init') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Validate') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform validate'
                }
            }
        }

        stage('Terraform Destroy Plan') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform plan -destroy -out=destroy.tfplan'
                }
            }
        }

        stage('Archive Destroy Plan') {
            steps {
                archiveArtifacts artifacts: 'destroy.tfplan', fingerprint: true
            }
        }

        stage('Manual Approval') {
            steps {
                input message: 'Approve Terraform Destroy?', ok: 'Destroy'
            }
        }

        stage('Terraform Destroy Apply') {
            steps {
                withCredentials([
                    string(credentialsId: 'aws-access-key-id', variable: 'AWS_ACCESS_KEY_ID'),
                    string(credentialsId: 'aws-secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform apply -auto-approve destroy.tfplan'
                }
            }
        }
    }

    post {

        success {
            echo 'Terraform Infrastructure destroyed successfully!'
        }

        failure {
            echo 'Terraform destroy failed!'
        }

        always {
            cleanWs()
        }
    }
}
