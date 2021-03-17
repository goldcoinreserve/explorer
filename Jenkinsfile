pipeline {
    agent { docker { image 'node:12-alpine' } }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm install --dev'
            }        
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }        
        }
        stage('Deploy on K8s cluster') {
            steps {
                acsDeploy azureCredentialsId: 'SH_85_subscription', configFilePaths: 'k8-deploy.yml', containerService: 'gcr-cluster | AKS', dcosDockerCredentialsPath: '', resourceGroupName: 'sh-k8s-rg', secretName: '', sshCredentialsId: 'f789f60a-6d11-43f4-85db-d298d4cf416b'
            }        
        }                
    }
}
