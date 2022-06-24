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
       environment {
          ANDROID_PUBLISHER_CREDENTIALS = """${sh(
          returnStdout: true,
          script: 'cat /Users/Guneet/StudioProjects/MyApplication/pc-api-6124060664771321122-615-00c14ec97d24.json'
          )}"""
      }
      steps {
        sh '''./gradlew publishBundle'''
      }
    }

  }
}