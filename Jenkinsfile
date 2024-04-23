pipeline {
    agent { 
        docker { 
            image 'python:3.8.16-bullseye' 
            args '-u root'
        }
    }
    stages {
        stage ("Run the script") {
            steps {
                script {
                    // Install required Python packages
                    sh "pip3 install -r requirements.txt"
                    
                    // Run the Python script with AWS credentials
                    withCredentials([[
                        $class: 'AmazonWebServicesCredentialsBinding',
                        credentialsId: 'aws-credentials', // Update this with your credentials ID
                        accessKeyVariable: 'AWS_ACCESS_KEY_ID', // Variable name for access key
                        secretKeyVariable: 'AWS_SECRET_ACCESS_KEY' // Variable name for secret key
                    ]]) {
                        sh "python3 check_endpoint.py"
                    }
                }
            }
        }
    }
}
