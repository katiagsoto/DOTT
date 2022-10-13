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
  stage('Build') {
     steps {
        git branch: 'master', url: git 'https://github.com/katiagsoto/DOTT.git'
      }
    }
    stage('test') {
      steps {
        sh 'python -m pytest'
      }   
    }
     stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
