pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Package') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Build Image') {
      steps {
        sh 'docker build -t registry-vpc.cn-beijing.aliyuncs.com/micro-java/$PROJECT .'
      }
    }
    stage('Push Image') {
      steps {
        sh 'docker push registry-vpc.cn-beijing.aliyuncs.com/micro-java/$PROJECT'
      }
    }
  }
  environment {
    PROJECT = 'micro-core-gateway'
  }
}