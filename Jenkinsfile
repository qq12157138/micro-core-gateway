pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('debug') {
      steps {
        sh '''pwd

mvn -B -DskipTests clean package

ls target'''
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