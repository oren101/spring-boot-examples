pipeline {
  agent any
  stages {
    stage('check out code') {
      steps {
        git(url: 'https://github.com/oren101/spring-boot-examples.git', branch: 'oren101-2_sol', changelog: true)
      }
    }

  }
}