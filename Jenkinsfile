pipeline {
    agent any
    stages{
        stage('build'){
            steps {
                sh 'mvn clean install'
            }
        }
	stage('clone'){
            steps {
                git 'C:\\Users\\mssql\\Rep\\'
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
			zip archive: true, dir: ", glob: ", zipFile:
			env.BUILD_DISPLAY_NAME+'_archive.zip'
		}
            }
        }
	stage('Unzip'){
            steps {
                unzip zipFile: env.BUILD_DISPLAY_NAME+'_archive.zip', dir:'C:\\Users\\mssql\\Rep\\'+env.BUILD_DISPLAY_NAME
            }
        }
	stage('Unzip'){
            steps {
                mail bcc: ",body: "test", cc: ",from: ",replyTo: ", subject: 'Pipeline Jenkins', to: 'eng48mar@gmail.com'
            }
        }
    }
    post {
        always {
            mail to :"recipient@company.com",
                subject: "New build report: ${currentBuild.fullDisplayName}",
                body:"Check out status at ${env.BUILD_URL}"
        }
    }
}