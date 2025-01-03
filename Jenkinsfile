pipeline {
    agent any

    environment {
        PATH = "/opt/maven3/bin:$PATH"
    }

    stages {
        stage("Git Checkout") {
            steps {
                git credentialsId: 'cc988b5f-9f92-4537-97f6-86679fc2d1ca', url: 'https://github.com/saikumar0503/123.git'
            }
        }
        stage("Maven Validate") {
            steps {
                sh "mvn validate"
            }
        }
        stage("Maven Test") {
            steps {
                sh "mvn test"
            }
        }
        stage("Maven Build") {
            steps {
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("Deploy to Tomcat") {
            steps {
                sh "cp target/myweb.war /opt/tomcat1/webapps/"
            }
        }
    }
}
