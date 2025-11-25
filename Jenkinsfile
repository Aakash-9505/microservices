pipeline {
    agent any

    tools{
        mvn='MAVEN_HOME'
    }

    stages {
        stage('git repo & clean') {
            steps {
                //bat "rmdir /s /q microservices" 
                bat "git clone https://github.com/Aakash-9505/microservices.git"
                bat "mvn clean -f microservices"
            }
        }
        
        stage('test') {
            steps {
                bat 'mvn install -f microservices'
            }
        }

        stage('test') {
            steps {
                bat 'mvn test -f microservices'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat 'copy target\\*.war "C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps\\microservices.war"'
            }
        }
    }

    post {
        success {
            echo 'App deployed successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}