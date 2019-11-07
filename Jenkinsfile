pipeline {
    agent any

    stages {    
        stage('Deploy') {
            steps {
            	bat 'mvn clean package deploy -DmuleDeploy'
                echo 'Deploying....'
            }
        }
    }
}