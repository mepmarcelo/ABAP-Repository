pipeline {
  agent any 
  stages {
    stage('Build') {
      steps {
        deleteDir()
        dir('sap-pipeline') {
          git credentialsId: 'GibHub', url: 'https://github.com/mepmarcelo/abap-ci-pipeline'
          echo 'Path: ${PATH}'
          sh 'node -v'
          sh 'npm -v'
          sh "npm install"
        }
      }
    }
    stage('ABAP Unit') {
      steps {
      dir('sap-pipeline') {
        sh 'npm run abapUnit'
        junit 'abap-unit/reports/*.xml'
      }
      }
    }
  }
}