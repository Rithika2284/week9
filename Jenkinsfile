pipeline{
    agent any
    stages
    {
        stage('Build Docker Image'){
            steps{
                echo "Build Docker Image"
                bat "docker build -t kubedemoapp:v1 ."
            }
        }
        stage('Docker Login'){
            steps{
                bat 'docker login -u vemularithika7 -p Rithika@22'
            }
        }
        stage('push Docker Image to Docker Hub'){
            steps{
                echo "push Docker Image to Docker Hub"
                bat "docker tag kubedemoapp vemularithika2284/week9:k2"
                bat "docker push vemularithika2284/week9:k2"
            }
        }
        stage('Deploy to Kubernetes'){
            steps{
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
    post {
        success {
            echo 'Successful'
        }
        failure {
            echo 'Unsuccessful'
        }
    }
}
