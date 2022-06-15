pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh ''' chmod +x gradlew
./gradlew clean
./gradlew assembleDebug'''
      }
    }

    stage('Save the Artifact') {
      steps {
        archiveArtifacts '**/*.apk'
      }
    }

    stage('Deploy') {
      environment {
        GOOGLE_APPLICATION_CREDENTIALS = '/Users/Guneet/Downloads/my-application-df283-5fa6fad7dfbe.json'
      }
      steps {
        sh './gradlew bundleDebug appDistributionUploadDebug --artifactType="APK"'
      }
    }

  }
}