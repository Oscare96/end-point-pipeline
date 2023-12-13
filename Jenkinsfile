pipeline {
    agent { 
      docker { image 'python:3.8.16-bullseye' }
    }
    stages {
       stage ("Run the script") {
            steps {
                withAWS(credentials: 'awscredID', region: 'us-east-1'){
                    sh "sudo pip3 install -r requirements.txt --user"
                    sh "sudo python3 check_endpoint.py"
                }
            }
        }
    }
}
