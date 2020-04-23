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
        withAWS(region: 'eu-central-1', credentials: 'aws-static') {
          sh 'echo "Upload index.html to S3 with AWS credentials"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'udacity-c4-static')
        }
      }
    }
  }
}