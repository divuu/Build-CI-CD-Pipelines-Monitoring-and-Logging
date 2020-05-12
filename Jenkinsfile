pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
          sh 'tidy -q -e *.html'
      }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(credentials:'s3-access-credential') {
        sh 'echo "Uploading content with AWS creds"'
            s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'my-s3-utkarsh')
        }
    }
  }
}
}