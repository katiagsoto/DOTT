node {
  stage('SCM') {
    checkout scm
  }
  
  stage('Build') {
        git 'https://github.com/katiagsoto/DOTT.git'
  }    
      
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqubescanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
  stage('test') {
    steps {
      sh 'python -m pytest'
      sh 'python test.py'
    }   
  }
} 
