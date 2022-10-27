pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipeline -t malkigu/todo-fe:latest --target builder .'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipeline -t malkigu/todo-fe:latest --target testing .'
            }
        }
        stage('Delivery') {
            steps {
                echo 'Delivery....'
                sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipeline -t malkigu/todo-fe:latest --target delivery .'
            }
        }
         stage('Cleanup') {
            steps {
                echo 'Cleanup....'
                sh 'docker system prune -f'
            }
        }
         stage('Push') {
            steps {
                echo 'pushing to dockerhub....'
                sh 'docker login -u malkigu -p Mg14102001'
                sh 'docker push malkigu/todo-fe:latest'
            }
        }
    }
}
