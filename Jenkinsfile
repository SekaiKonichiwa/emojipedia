pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        checkout scm
      }
    }

    stage('Build React App') {
      agent {
        docker {
          image 'node:18'
          args '-u root'  // run as root user inside container to avoid permission issues
        }
      }
      steps {
        sh 'npm install'
        sh 'npm run build'
        // archive build folder to use outside container
        sh 'cp -r dist ../dist_for_deploy'
      }
    }

    stage('Deploy
