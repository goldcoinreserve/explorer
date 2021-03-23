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
                script {
                kubernetesDeploy(
                    configs: 'k8-deploy.yml',
                    kubeconfigId: 'kubernetes',
                    enableConfigSubstitution: false
                    )           
               
                }
            }        
        }                
    }
}
