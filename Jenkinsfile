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

    stage('Post-build Actions') {
      steps {
        archiveArtifacts '**/*.apk'
      }
    }

  }
}