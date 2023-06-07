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
        stage('Log in to dockerHub And Push Image'){
            steps {
                echo "DockerHub login in progress..."
                withCredentials([usernamePassword(credentialsId:'dockerHub',
                passwordVariable:'dockerHubPass',usernameVariable:'dockerHubUser')])
                {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                    sh 'docker push shubhambmatere/node-todo-cicd-app:latest'
                }
            }
        }
        stage('Deploy'){
            steps {
               echo "Deployment in progress..."
               sh 'docker-compose down && docker-compose up -d'
                }
             }
         }
    }
