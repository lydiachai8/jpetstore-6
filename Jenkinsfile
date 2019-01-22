pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install -Dlicense.skip=true'
      }
    }
    stage('Testing') {
      parallel {
        stage('SonarQube Test') {
          steps {
            sh '''mvn sonar:sonar -Dsonar.host.url=http://<IP address>:8081 -Dlicense.skip=true
'''
          }
        }
        stage('Print Tester Credentials') {
          steps {
            echo 'The tester is ${TESTER}'
            sleep 10
          }
        }
      }
    }
  }
  tools {
    maven 'maven'
  }
}