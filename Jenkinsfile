pipeline {
  agent {
    node {
      label 'Centos_nodejs'
    }

  }
  stages {
    stage('check out code') {
      steps {
        git(url: 'https://github.com/oren101/spring-boot-examples.git', branch: 'oren101-2_sol', changelog: true, poll: true)
      }
    }

    stage('maven compile') {
      steps {
        sh '''cd spring-boot-package-war/
mvn compile'''
      }
    }

    stage('test') {
      steps {
        sh '''cd spring-boot-package-war/



mvn test'''
      }
    }

    stage('incremant') {
      steps {
        sh '''cd spring-boot-package-war/

mvn build-helper:parse-version versions:set -DnewVersion=0.0.2.$BUILD_ID-SNAPSHOT versions:commit'''
      }
    }

    stage('packege  [mvn clean packege]') {
      steps {
        sh '''cd spring-boot-package-war/


mvn clean package'''
      }
    }

    stage('MS Slack') {
      steps {
        slackSend()
      }
    }

  }
}