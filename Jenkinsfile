pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install -Dlicense.skip=true'
      }
    }
    stage('Testing') {
      steps {
        sh '''mvn sonar:sonar -Dsonar.host.url=http://<IP address>:8081 -Dlicense.skip=true
'''
      }
    }
  }
  tools {
    maven 'maven'
  }
}