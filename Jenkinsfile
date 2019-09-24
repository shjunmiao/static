pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                bat 'echo "tidy -q -e index.html"'
            }
        }
        stage('Upload to AWS') {
            steps {
                withAWS(region:'us-east-2',credentials:'aws-static') {
		    bat 'echo "Hello World with AWS creds"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'shjunmiao-static-jenkins-pipeline')
                }
            }
        }
    }
}
