/*pipeline {
    agent { 
      docker { image 'python:3.8.16-bullseye' }
    }
    stages {
       stage ("Run the script") {
            steps {
                withAWS(credentials: 'awscredID', region: 'us-east-1'){
                    user('root')
                    sh "pip3 install -r requirements.txt"
                    sh "python3 check_endpoint.py"
                }
            }
        }
    }
}*/
pipeline {
    agent { 
        docker { image 'python:3.8.16-bullseye' }
    }
    stages {
        stage ("Run the script") {
            steps {
                script {
                    // Run the following block as root
                    user('root') {
                        withAWS(credentials: 'awscredID', region: 'us-east-1') {
                            sh "pip3 install -r requirements.txt"
                            sh "python3 check_endpoint.py"
                        }
                    }
                }
            }
        }
    }
}
