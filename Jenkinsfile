pipeline {
    agent any
    stages{
	stage('checkout'){
            steps {
		checkout([$class: 'GitSCM', branches: [[name: 'master']], extensions: [], userRemoteConfigs: [[credentialsId: 'e7c4e7f8-a755-4dfc-822b-8bb00e45198e', url: 'https://github.com/Noname008/test.git']]])
            }
        }
	stage('build'){
            steps {
                bat 'mvn compile'
            }
        }
    }
    post {
        always {
           	mail bcc: '', body: 'test', cc: '', from: '', replyTo: '', subject: 'jenkins', to: 'eng48mar@gmail.com'
        }
    }
}