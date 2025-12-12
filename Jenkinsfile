pipeline {
    agent any
    environment {
        TF_VAR_gcp_project = "qwiklabs-gcp-00-8467f2a5008b" // REPLACE WITH YOUR PROJECT ID FROM QWIKLABS
    }
    stages {
        stage("Configure Cluster") {
            steps {
                script {
                    dir('terraform') {
                        withCredentials([file(credentialsId: 'gcp_credentials', variable:'GCP_CREDENTIALS')]) {
                            sh '''
                            export GOOGLE_APPLICATION_CREDENTIALS=$GCP_CREDENTIALS
                            terraform init
                            terraform apply -auto-approve
                            '''
                        }
                    }
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
