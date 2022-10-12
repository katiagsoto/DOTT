node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqubescanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
pipeline {
  agent any
 
  tools {jenkins.plugins.shiningpanda.tools.PythonInstallation "python"}
 
  stages {
    stage('Example') {
      steps {
        sh 'pip config ls'
      }
    }
  }
}
