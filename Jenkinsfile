pipeline {
    agent any
    stages {
        stage('Lint HTML & Dockerfile'){
            steps {
                sh 'tidy -q -e blue-green/blue/*.html'
                sh 'tidy -q -e blue-green/green/*.html'
                // sh 'docker pull hadolint'
                sh 'hadolint blue-green/blue/Dockerfile'
                sh 'hadolint blue-green/green/Dockerfile'
            }
        }
        stage('Build and Publish Docker Image'){
                    steps {
                        sh 'docker build -t kruthiga/blueimage -f blue-green/blue/Dockerfile blue-green/blue'
                        sh 'docker build -t kruthiga/greenimage -f blue-green/green/Dockerfile blue-green/green'
                        sh 'docker push kruthigagopalan/blueimage'
                        sh 'docker push kruthigagopalan/greenimage'
                        sh 'docker rmi -f kruthiga/greenimage'
                        sh 'docker rmi -f kruthiga/blueimage'
                    }
                }
    }
}
