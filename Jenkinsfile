pipeline {
    agent any

    stages {
        stage('code') {
            steps {
                git "https://github.com/greesh123-queen/myfirstdockerproject.git"
            }
        }
        stage('build'){
            steps{
                sh 'docker build -t myimg:v1 .'
            }
        }
        stage('registry'){
            steps{
                
                withDockerRegistry(credentialsId: '29346708-f573-4a35-9622-698c39f7c5e4') {
                    sh 'docker tag myimg:v1 masanamgreeshma/myrepo2:appv1'
                    sh 'docker push masanamgreeshma/myrepo2:appv1'
                }
            }
        }
        stage('deploy'){
            steps{
                sh 'docker run -itd --name cont1 -p 1111:80 masanamgreeshma/myrepo2:appv1'
            }
        }
    }
}

