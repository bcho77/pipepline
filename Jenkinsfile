pipeline{
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('vaninoel')
    }
    stages{
        stage{
            steps(checkout){

               git'https://github.com/bcho77/pipepline.git'
            }
        }
        stage{
            steps('Build image'){
                sh 'sudo docker build -t vaninoel/pipepline:$BUILD_NUMBER .'
            }
        }
        stage{
            steps('Login to dockerhub'){
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage{
            steps('Push to dockerhub'){
                sh 'sudo docker push vaninoel/pipeline:$BUILD_NUMBER'
            }
        }
        
    }post{
        always{
            sh 'sudo docker logout'
        }
    }
}