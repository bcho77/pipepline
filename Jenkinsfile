pipeline{
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('vaninoel')
    }
    stages{
        stage(checkout){
            steps{

               git'https://github.com/bcho77/pipepline.git'
            }
        }
        stage('Build image') {
            steps{
                sh 'sudo docker build -t vaninoel/pipepline:$BUILD_NUMBER .'
            }
        }
        stage('Login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push to dockerhub') {
            steps{
                sh 'sudo docker push vaninoel/pipepline:$BUILD_NUMBER'
            }
        }
        
    }
    post{
        always{
            sh 'sudo docker logout'
        }
    }
}
