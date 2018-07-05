pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Package') {
      parallel {
        stage('Package') {
          agent {
            docker {
              image 'maven:3-alpine'
              args '-v /root/.m2:/root/.m2'
            }

          }
          steps {
            sh 'mvn -B -DskipTests clean package'
          }
        }
        stage('debug') {
          steps {
            sh 'ls target'
          }
        }
      }
    }
    stage('Image') {
      steps {
        sh '''pwd

docker build -t $JOB_NAME .'''
      }
    }
  }
}