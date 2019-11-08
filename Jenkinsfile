pipeline {
    agent any
    stages{
    	stage ('deploy'){
    		steps {
            	bat 'mvn clean package deploy -DmuleDeploy'
                echo 'Deplegando ando....'
            }
    	}
    }
}