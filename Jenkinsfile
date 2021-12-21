pipeline {
    agent any
    stages{
	stage('build'){
            steps {
                git 'C:\\Users\\mssql\\Documents\\GitHub\\simple_maven\\'
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
			zip archive: true, dir: '', glob: '', zipFile:env.BUILD_DISPLAY_NAME+'_archive.zip'
		}
            }
        }
	stage('unzip'){
            steps {
                unzip zipFile: env.BUILD_DISPLAY_NAME+'_archive.zip', dir:'C:\\Users\\mssql\\Rep\\'+env.BUILD_DISPLAY_NAME
            }
        }
	stage('mail'){
            steps {
                mail bcc: '',body: 'test', cc: '',from: '',replyTo: '', subject: 'Pipeline Jenkins', to:'eng48mar@gmail.com'
            }
        }
    }
}