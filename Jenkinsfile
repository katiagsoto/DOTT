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


  stage('Test') {
        git 'https://github.com/katiagsoto/DOTT.git'
        
    def pyHome = tool 'python'
    withpytest(){
    sh 'python3 -m pytest'
   }
 }
