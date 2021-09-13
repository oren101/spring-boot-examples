pipeline {
  agent {
    node {
      label 'master'
    }
 }
  stages {
    stage('CheckoutCode') {
      steps {
        git(url: 'https://github.com/oren101/spring-boot-examples.git', branch: ' oren101-2_sol ', changelog: true)
      }
    }

    stage('mvn compile') {
      steps {
        sh '''cd spring-boot-package-war
mvn compile'''
      }
    }

    stage('Test {mvn test}') {
      steps {
        sh '''cd spring-boot-package-war
mvn test'''
      }
    }

    stage('Package {mvn clean package}') {
      steps {
        sh '''cd spring-boot-package-war
mvn clean package'''
      }
    }

    stage('\'Increment-pom file\'') {
      steps {
        sh '''cd spring-boot-package-war
mvn build-helper:parse-version versions:set -DnewVersion=0.0.2.$BUILD_ID-SNAPSHOT versions:commit
'''
      }
    }
  }
}
