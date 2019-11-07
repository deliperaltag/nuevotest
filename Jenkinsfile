pipeline {
    agent any
	stage('Build') {
            node {
    			checkout scm
			    sh 'bundle install'
				sh 'bundle exec rake build spec'
			    archive (includes: 'pkg/*.gem')
			    publishHTML ([
			        allowMissing: false,
			        alwaysLinkToLastBuild: false,
			        keepAll: true,
			        reportDir: 'coverage',
			        reportFiles: 'index.html',
			        reportName: "RCov Report"
			      ])

 				 }
        }
    stage('Test') {
            steps {
            	sh './gradlew check'
                echo 'Testing..'
            }
     }
    stages {    
        stage('Deploy') {
            steps {
            	bat 'mvn clean package deploy -DmuleDeploy'
                echo 'Deploying....'
            }
        }
    }
}