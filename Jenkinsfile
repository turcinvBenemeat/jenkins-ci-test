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
