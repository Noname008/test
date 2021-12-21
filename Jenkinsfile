pipeline {
    agent any
    stages{
	stage('checkout'){
            steps {
		checkout([$class: 'GitSCM', branches: [[name: '*/master']],extensions: [], userRemoteConfigs: [[url: 'https://github.com/Noname008/test']]])
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
           	mail bcc: '',
		body: 'test', 
		cc: '',from: '',
		replyTo: '', 
		subject: 'Pipeline Jenkins', 
		to:'eng48mar@gmail.com'
        }
    }
}