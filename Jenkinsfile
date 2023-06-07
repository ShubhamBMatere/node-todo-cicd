pipeline{
    agent { label  'image-push-agent'}
    
    stages{
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
