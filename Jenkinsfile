pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh ''' chmod +x gradlew
./gradlew clean
./gradlew bundleRelease'''
      }
    }

    stage('Save the Artifact') {
      steps {
        archiveArtifacts '**/*.aab'
      }
    }

    stage('Deploy on Playstore') {
      steps {
        androidApkUpload(googleCredentialsId: 'avishkar_google_play_key', trackName: 'internal-app-sharing')
      }
    }

  }
}