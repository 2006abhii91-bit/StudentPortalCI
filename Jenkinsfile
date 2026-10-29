pipeline {
    agent any
    stages {
        stage('clone') 
        {
            steps {
                git branch: 'master', url: 'https://github.com/2006abhii91-bit/StudentPortalCI.git'
            }
        }
        stage('build') 
        {
            steps {
                bat ' echo docker build -t %DOCKER_IMAGE%:%DOCKER_TAG% .'
            }
        }

        stage('login')
        {
            steps {
                withCredentials([usernamePassword
                (credentialsId: 'DOCKEHUB_PAT',
                 usernameVariable: 'DOCKER_USERNAME',
                  passwordVariable: 'DOCKER_PASSWORD')]) 
                bat ' echo docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
                
               
            }
        }

        stage('push') 
        {
            steps {
                bat ' echo docker push %DOCKER_IMAGE%:%DOCKER_TAG%'
            }
        }
    }

        post{
            success{
                echo 'success'
            }
            failure{
                echo 'failure'
            }
        }
    }
     
