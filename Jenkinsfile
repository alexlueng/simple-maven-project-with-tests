node('master') {
  checkout scm
  stage('build') {
    withMaven(maven:'M3') {
      if(isUnix()) {
        sh 'mvn -Dmaven.test.failure.ingore clean package'
      }
      else {
        bat 'mvn -Dmaven.test.failure.ingore clean package'
      }
    }
  }
  stage('Results') {
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }
}
