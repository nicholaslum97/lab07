pipeline {
  agent any
  stages {


    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('OWASP DependencyCheck') {
      steps {
        dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'default'
      }
    }
  }

  post {
    success {
      dependencyCheckPublisher pattern: 'dependency-check-report.xml'
    }
  }
}
