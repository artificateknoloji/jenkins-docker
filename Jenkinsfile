pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    TIMESTAMP=${BUILD_TIMESTAMP}
  //  DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    /*
    stage('Build') {
      steps {
        sh 'docker build -t artifica/jenkins-docker-hub .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    */
    stage('Build') {
      steps {
        sh "docker build -t aic-storage.us-west4-b.c.aicommerce-371409.internal:5000/jenkins-docker-hub:${TIMESTAMP} -t aic-storage.us-west4-b.c.aicommerce-371409.internal:5000/jenkins-docker-hub:latest ."
      }
    }
    stage('Push') {
      steps {
        sh "docker push aic-storage.us-west4-b.c.aicommerce-371409.internal:5000/jenkins-docker-hub:${TIMESTAMP} aic-storage.us-west4-b.c.aicommerce-371409.internal:5000/jenkins-docker-hub:latest"
      }
    }
  }
  /*post {
    always {
      sh 'docker logout'
    }
  }*/
}