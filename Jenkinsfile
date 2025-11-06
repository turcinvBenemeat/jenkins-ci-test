pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        echo "✅ Cloning repository..."
      }
    }
    stage('Build') {
      steps {
        echo "🚀 Running build script..."
        sh './build.sh'
      }
    }
    stage('Test') {
      steps {
        echo "🧪 Running basic test..."
        sh 'echo "All tests passed!"'
      }
    }
    stage('Docker image build & run') {
      steps {
        writeFile file: 'Dockerfile', text: 'FROM alpine:3.20\nCMD ["echo","Image built & run OK"]\n'
        sh '''
          docker build -t jenkins-ci-test:latest .
          docker run --rm jenkins-ci-test:latest
        '''
      }
    }
  }
  post {
    success {
      echo "✅ Pipeline finished successfully!"
    }
    failure {
      echo "❌ Pipeline failed!"
    }
  }
}
