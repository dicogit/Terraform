pipeline {
    agent any 
    stages {
        stage ("TF Creating EC2") {
            environment {
                AWS_ACCESS_KEY_ID=credentials("AWS_ACCESS_KEY_ID")
                AWS_SECRET_ACCESS_KEY=credentials("AWS_SECRET_ACCESS_KEY")
            }
            steps {
                script {
                    sh "terraform init"
                    sh "terraform apply --auto-approve"
                    EC2_PUBLIC_IP=sh(returnStdout: true, script: "terraform output ip").trim()
                    echo "EC2_PUBLIC_IP: '${EC2_PUBLIC_IP}'"
                }
            }
        }
    }
}