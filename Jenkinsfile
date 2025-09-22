pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build') {
      steps { sh './mvnw -B clean package' }
    }
    stage('Unit tests') {
      steps { junit '**/target/surefire-reports/*.xml' }
    }
    stage('Archive') {
      steps { archiveArtifacts artifacts: 'target/*.jar', fingerprint: true }
    }
  }

  post {
    always { echo "Build terminé" }
  }
}
