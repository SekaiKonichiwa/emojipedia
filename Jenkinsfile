stage('Checkout Code') {
  steps {
    checkout scm
  }
}

pipeline {
  agent any

  stages {
    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build React App') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Deploy Build') {
      steps {
        sh 'rm -rf /var/www/html/*'
        sh 'cp -r build/* /var/www/html/'
      }
    }
  }
}
