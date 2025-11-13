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
                sh '''
                echo "No build required for plain JS project."
                ls -l
                '''
            }
        }

        stage('Deploy to AWS S3') {
            steps {
                withAWS(credentials: 'aws-creds', region: 'ap-south-1') {
                    sh '''
                    echo "Deploying static site to S3..."
                    aws s3 cp . s3://bucketkulla-edukuda-thanni --recursive --exclude ".git/*"
                    '''
                }
            }
        }
    }
}
