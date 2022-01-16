pipeline {
    agent any
    stages{
	stage('Checkout'){
            steps {
		checkout([$class: 'GitSCM', branches: [[name: '*/master']],extensions: [], userRemoteConfigs: [[url: 'https://github.com/Noname008/test']]])
            }
        }
	stage('Build'){
            steps {
		bat "mvn compile"
            }
        }
	stage('Test'){
            steps {
                bat "mvn test"
            }
        }
	stage('Archive'){
            steps {
                script{
			bat "mvn -Dbuild_version=${build_version} package"
		}
            }
        }
	stage('Mail'){
            steps {
                mail bcc: '',body: 'test', cc: '',from: '',replyTo: '', subject: 'Pipeline Jenkins', to:'eng48mar@gmail.com'
            }
        }
	stage('Publish'){
            steps {
                bat "move /Y \"${workspace}\\target\\jenkins-simple-*\" C:\\test"
            }
        }
    }
}