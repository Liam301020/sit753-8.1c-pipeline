pipeline {
  agent any

  triggers {
    // Automatic checking new commit (2p/1times)
    pollSCM('H/2 * * * *')
  }

  stages {
    stage('Build') { steps { echo 'Build: compile & package (Maven/Gradle/npm)' } }
    stage('Unit & Integration Tests') { steps { echo 'Run unit & integration tests (JUnit/Jest/Postman)' } }
    stage('Code Analysis') { steps { echo 'Static code analysis (SonarQube/ESLint/Checkstyle)' } }
    stage('Security Scan') { steps { echo 'Security scan (npm audit/Snyk/OWASP)' } }
    stage('Deploy to Staging') { steps { echo 'Deploy to staging (AWS EC2/SSH/Ansible)' } }
    stage('Integration Tests on Staging') { steps { echo 'Run integration tests in staging (Cypress/Selenium)' } }
    stage('Deploy to Production') { steps { echo 'Deploy to production (Ansible/Helm/ArgoCD)' } }
  }
}
post {
    success {
      emailext(
        subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
        body: """Build thành công!
- Job   : ${env.JOB_NAME}
- Build : #${env.BUILD_NUMBER}
- Link  : ${env.BUILD_URL}""",
        to: 'nguyengialam301020@gmail.com'
      )
    }
    failure {
      emailext(
        subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
        body: """Build thất bại!
- Job   : ${env.JOB_NAME}
- Build : #${env.BUILD_NUMBER}
- Link  : ${env.BUILD_URL}""",
        to: 'nguyengialam301020@gmail.com'
      )
    }
  }