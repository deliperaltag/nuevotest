pipeline {
    agent any
    stages{
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
				        reportFiles: 'probandomunit-report.html',
				        reportName: "probandomunit-report"
				      ])
	
	 			 }
	     }
	     stage('Deploy') {
	            steps {
	            	bat 'mvn clean package deploy -DmuleDeploy'
	                echo 'Deploying....'
	            }
	     }
    }
}