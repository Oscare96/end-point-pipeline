pipeline {
    agent { 
      docker { image 'python:3.8.16-bullseye' }
    }
    stages {
       stage ("Run the script") {
            steps {
                withAWS(credentials: 'awscredID', region: 'us-east-1'){
                    sh "mkdir -p $HOME/.pip_cache"
                    sh "pip3 install --cache-dir=$HOME/.pip_cache -r requirements.txt"
                    sh "python3 check_endpoint.py"
                }
            }
        }
    }
}
