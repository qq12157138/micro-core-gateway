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
    stage('Image') {
      steps {
        sh '''docker build -t registry.cn-hangzhou.aliyuncs.com/micro-java/$JOB_NAME .

docker push registry.cn-hangzhou.aliyuncs.com/micro-java/$JOB_NAME'''
      }
    }
  }
}