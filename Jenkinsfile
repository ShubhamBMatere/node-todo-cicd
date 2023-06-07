pipeline{
    agent { label  'dev-build-agent'}
    
    stages{
        stage('Build'){
            steps {
                git url: 'https://github.com/ShubhamBMatere/node-todo-cicd.git', branch : 'master'
            }
        }
        stage('Build And Test'){
            steps {
                echo "Building and testing in progress..."
                sh 'docker build . -t shubhambmatere/node-todo-cicd-app:latest'
            }
        }
         }
    }
