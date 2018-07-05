pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('debug') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Image') {
      agent any
      steps {
        sh 'docker build -t $JOB_NAME .'
      }
    }
  }
}