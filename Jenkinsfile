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

  }
}