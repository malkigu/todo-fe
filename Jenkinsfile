pipeline {
    agent any
    environment {
        BITBUCKET_COMMON_CREDS_USR = credentials('jenkins-user-for-artifact-repository')
        BITBUCKET_COMMON_CREDS_PSW = credentials('jenkins-user-for-artifact-repository')
    }
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
                sh 'docker login -u $BITBUCKET_COMMON_CREDS_USR -p $BITBUCKET_COMMON_CREDS_PSW'
                sh 'docker push malkigu/todo-fe:latest'
            }
        }
    }
}
