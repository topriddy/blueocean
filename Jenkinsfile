pipeline {
  agent any 
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World" '
        sh """
                echo 'Multiline shell steps works too'
                ls -lah
            """
      }
    }
    stage('Lint HTML'){
        steps {
            sh 'tidy -q -e *.html'
        }
    }
     stage('Upload to AWS'){
        steps {
            withAWS(region: 'us-east-2', credentials: 'MyCredentials'){
                s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'hello.html', bucket: 'topriddy-c3pipelines')
            }
        }
    }
  }
}