pipeline {
    agent { 
      docker { image 'python:3.8.16-bullseye' }
    }
    stages {
       stage ("Run the script") {
            steps {
                withAWS(credentials: 'awscredID', region: 'us-east-1'){
                    sh "pip install -r requirements.txt"
                    sh "python check_endpoint.py"
                }
            }
        }
    }
}
