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

    stage('Deploy on Playstore') {
      steps {
        androidApkUpload(googleCredentialsId: 'avishkar_google_play_key', trackName: 'internal-app-sharing')
      }
    }

  }
}