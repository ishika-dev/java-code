pipeline {
    agent any
    stages {
        stage("Checkout") {   
            steps {               	 
                git branch: 'main', url: 'https://github.com/ishika-dev/java-code.git'        	 
            }    
        }
        stage('Maven Clean') {
            steps {
                sh "mvn clean"  	 
            }
        }
        stage('Maven Build') {
            steps {
                sh "mvn compile"  	 
            }
        }
        stage("Unit Test") {          	 
            steps {  	 
                sh "mvn test"          	 
            }
        }
        stage("Maven Package") {
            steps {
                sh "mvn package"
            }
        }
        stage('deploy to tomcat') {
            steps {
              deploy adapters: [tomcat9(credentialsId: 'admin', path: '', url: 'http://54.175.208.126:8080')], contextPath: 'app', war: '**/target/*.war'
            }
        }
    }
}   


 
 


