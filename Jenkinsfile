pipeline {
  agent {
    node {
      label 'Centos_nodejs'
    }

  }
  stages {
    stage('Clean Workspace') {
      steps {
        cleanWs()
      }
    }

    stage('Checkout code') {
      steps {
        git(url: 'https://github.com/oren101/spring-boot-examples.git', branch: ' oren101-2_sol ', changelog: true)
      }
    }

    stage('Compile maven') {
      steps {
        sh '''cd spring-boot-package-war/
mvn compile'''
      }
    }

    stage('Test maven') {
      steps {
        sh '''cd spring-boot-package-war/
mvn test'''
      }
    }

    stage('Increment POM') {
      steps {
        sh '''cd spring-boot-package-war/
 mvn build-helper:parse-version versions:set -DnewVersion=0.0.2.$BUILD_ID-SNAPSHOT'''
      }
    }

    stage('Package') {
      steps {
        sh '''cd spring-boot-package-war/
mvn clean package'''
      }
    }


        stage('Chuck norris') {
          steps {
            chuckNorris()
          }
    }
  }
}
