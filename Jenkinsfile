pipeline {
    agent any
    stages{
        stage('build'){
            steps {
                sh 'mvn clean install'
            }
        }
    }
    post {
        always {
            mail to :"eng48mar@gmail.com",
                subject: "New build report: ${currentBuild.fullDisplayName}",
                body:"Check out status at ${env.BUILD_URL}"
        }
    }
}