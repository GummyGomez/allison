pipeline {
    agent  any;
    stages {
        stage('Preparing the environment') {
            steps {
                sh 'echo El "hostname es $HOSTNAME y el ususarios es $USER"' 
                sh 'python3 -m pip install -r requirements.txt'
            }
        }
        stage('Code Quality') {
            steps {
                sh 'echo El "hostname es $HOSTNAME y el ususarios es $USER"'
                sh 'python3 -m pylint app.py'
            }
        }
        stage('Tests') {
            steps {
                sh 'echo El "hostname es $HOSTNAME y el ususarios es $USER"'
                sh 'python3 -m pytest'
            }
        }
   
    stage('Build') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'echo El "hostname es $HOSTNAME y el ususarios es $USER"'
              sh 'docker build https://github.com/AlissonMMenezes/Chapter10.git -t chapter10:latest'
          }
      }        
      stage('Deploy') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'echo "el hostname es $HOSTNAME y el usuario es $USER"'
              sh 'docker run -tdi -p 5000:5000 chapter10:latest'
          }
      }
    }

}

