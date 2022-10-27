pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'DOCKER_BUILDKIT=1 docker build -t malkigu/todo-fe:latest --target builder .'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'DOCKER_BUILDKIT=1 docker build -t malkigu/todo-fe:latest --target testing .'
            }
        }
        stage('Deploy') {
            steps {
                echo 'delivery....'
                sh 'DOCKER_BUILDKIT=1 docker build -t malkigu/todo-fe:latest --target deliverydelivery .'
            }
        }
    }
}
