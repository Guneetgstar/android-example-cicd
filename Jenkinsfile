pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh ''' chmod +x gradlew  
 ./gradlew clean  
 ./gradlew assembleDebug  '''
      }
    }

    stage('Save Artifact') {
      steps {
        archiveArtifacts '**/*.apk'
      }
    }

    stage('Deploy') {
      environment {
        GOOGLE_APPLICATION_CREDENTIALS = './my-application-df283-d006b2200276.json'
      }
      steps {
        sh '''./gradlew bundleDebug appDistributionUploadDebug
    --artifactType="APK"'''
      }
    }

  }
}