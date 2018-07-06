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
    stage('Build') {
      steps {
        sh 'docker build -t $JOB_NAME .'
      }
    }
  }
}