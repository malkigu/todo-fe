pipline {
  agent any
  
  stages{
    stage ('build') {
      steps {
        echo ''
        sh 'DOCKER_BUILDKIT=1 docker build -t malkigu:latest --target builder .'
      }
    }
  }
}
