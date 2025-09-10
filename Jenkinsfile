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
