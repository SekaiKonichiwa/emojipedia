pipeline {
  agent {
    docker {
      image 'node:18'  // Official Node.js image
    }
  }

  stages {
    stage('Checkout Code') {
      steps {
        checkout scm
      }
    }

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
        sh 'cp -r dist/* /var/www/html/'
      }
    }
  }
}
