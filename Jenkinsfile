pipeline {
  agent any
  
  stages {
    stage('Unit Test') { 
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
      steps {
        sh 'mvn deploy -DmuleDeploy -e -Dmule.version=4.4.0 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW}' 
      }
    }
  }
}
