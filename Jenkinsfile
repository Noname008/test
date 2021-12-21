pipeline {
    agent any
    tools{
	maven "maven 3.8.4"
	jdk "jdk17"
    }
	environment{
	build_version = "${BUILD_NUMBER}"
    }
    stages{
	stage('checkout'){
            steps {
		checkout([$class: 'GitSCM', branches: [[name: '*/master']],extensions: [], userRemoteConfigs: [[url: 'https://github.com/Noname008/test']]])
            }
        }
	stage('build'){
            steps {
		bat "mvn compile"
            }
        }
	stage('test'){
            steps {
                bat "mvn test"
            }
        }
	stage('archive'){
            steps {
                script{
			bat "mvn -Dbuild_version=${build_version} package"
		}
            }
        }
	stage('mail'){
            steps {
                mail bcc: '',body: 'test', cc: '',from: '',replyTo: '', subject: 'Pipeline Jenkins', to:'eng48mar@gmail.com'
            }
        }
	stage('publish'){
            steps {
                bat "move /Y \"${workspace}\\target\\jenkins-simple-*\" C:\\test"
            }
        }
    }
}