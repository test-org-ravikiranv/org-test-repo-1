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
        sh 'mvn clean -DskipTests=true install'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit Test') {
          steps {
            sh 'mvn test -Dtest=**/*Tests'
          }
        }

        stage('Integration Test') {
          steps {
            sh 'mvn clean verify'
          }
        }

      }
    }

    stage('Junit Result Archieve') {
      steps {
        junit(allowEmptyResults: true, testResults: '**/target/surefire-reports/TEST-*.xml')
      }
    }

  }
  tools {
    maven 'M3'
  }
}