pipeline{
    agent any
      environment {
        STACK_NAME = 'sam-app-beta-stage'
        S3_BUCKET = 'sam-jenkins-demo-us-west-2-user1'
      }  
    stages {
        stage('checkout') {
             steps { 
                 git branch: 'master',  url: 'https://github.com/ahafarag/tf-demo'
             }
        }
        stage('tf init')  {
            steps {
                    withAWS(credentials: 'aws', region: 'us-east-2') {
                    sh 'terraform init'
                    }
            }
        }
        stage('tf apply')  {
            steps {
                withAWS(credentials: 'aws', region: 'us-east-2'){
                sh 'terraform apply --auto-approve'
                }
            }
        }
    }
}
