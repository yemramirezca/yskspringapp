pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh './mvnw clean install -DskipTests'
      }
    }

    stage('test') {
      steps {
        sh './mvnw test'
      }
    }

     stage('Build Docker image') {
         steps {
             sh 'docker build -t yemramirezca/spring-boot-api-example:0.1.0-SNAPSHOT .'
         }
     }
     
     stage('Push Docker image') {
         environment {
             DOCKER_HUB_LOGIN = credentials('docker-hub')
         }
         steps {
             sh 'docker login --username=$DOCKER_HUB_LOGIN_USR --password=$DOCKER_HUB_LOGIN_PSW'
             sh 'docker push yemramirezca/spring-boot-api-example:0.1.0-SNAPSHOT'
         }
     }

  }
}
