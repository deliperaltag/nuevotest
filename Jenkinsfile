pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
            	sh './gradlew build'
                echo 'Building..'               
            }
        }
        stage('Test') {
            steps {
            	sh './gradlew check'
                echo 'Testing..'
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