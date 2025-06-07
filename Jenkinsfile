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
          args '-u root'  // run as root inside container
        }
      }
      steps {
        sh 'npm install'
        sh 'npm run build'
        sh 'cp -r dist dist_for_deploy'  // copy inside workspace
      }
    }

    stage('Deploy Build') {
      steps {
        sh """
          rm -rf /var/www/html/*
          cp -r dist_for_deploy/* /var/www/html/
        """
      }
    }
  }
}
