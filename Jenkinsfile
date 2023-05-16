pipeline{
    agent any
    environment {
        NEWRELIC_API_KEY = credentials('aws')
    }    
    stages {
        stage('checkout') {
             steps { 
                 git branch: 'master',  url: 'https://github.com/ahafarag/tf-demo'
             }
        }
        stage('tf init')  {
            steps {
                    sh 'terraform init'
            }
        }
        stage('tf apply')  {
            steps { 
                sh 'terraform apply --auto-approve'
            }
        }
    }
}
