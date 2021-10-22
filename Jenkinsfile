pipeline {
  agent any
  stages {
    stage('SCM Clone Repository') {
      steps {
        git(url: 'https://github.com/ravikirankiran097/Spring-PetClinic.git', branch: 'main', credentialsId: 'GitHub_Cred')
      }
    }

    stage('Build & Test') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true -Dcheckstyle.skip clean package'
      }
    }

  }
  tools {
    maven 'M3'
  }
}