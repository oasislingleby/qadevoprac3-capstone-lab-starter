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
                            // TODO: fill in the steps necessary to:
                            terraform init ()
                            terraform apply -auto-approve
                            // - provision the defined resources
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
