pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'ap-south-1'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Yogeshwari-MP/cab-booking.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building application..."'
                // Add build commands here (npm install, mvn package, etc.)
            }
        }

        stage('Deploy to AWS S3') {
            steps {
                withAWS(credentials: 'aws-creds', region: 'us-east-1') {
                    sh '''
                    echo "Deploying to AWS S3..."
                    aws s3 cp ./dist s3://bucketkulla-edukuda-thanni --recursive
                    '''
                }
            }
        }
    }
}
