pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('Build') {
      parallel {
        stage('Package') {
          steps {
            sh 'mvn -B -DskipTests clean package'
          }
        }
        stage('Image') {
          steps {
            sh 'docker build -t $JOB_NAME .'
          }
        }
      }
    }
  }
}