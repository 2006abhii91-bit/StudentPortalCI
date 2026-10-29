pipeline {
    agent any

     environment {
        DOCKER_IMAGE = '2006abhii91/exp'
       
    }
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
                bat 'echo %DOCKER_PASSWORD%|docker login -u 2006abhii91 --password-stdin'
                
               
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
     
