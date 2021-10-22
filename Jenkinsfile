pipeline {
  agent any
  stages {
    stage('SCM Clone Repository') {
      steps {
        git(url: 'https://github.com/ravikirankiran097/Spring-PetClinic.git', branch: 'main', credentialsId: 'GitHub_Cred')
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }

  }
  tools {
    maven 'M3'
  }
}