pipeline{
    agent any
    tools{
        maven "maven-398"
    }
    stages{
        stage('Check Maven'){
            steps{
                sh "if ! command -v mvn; then echo 'Maven not found!;' exit 1; fi"
            }
        }
        stage('Build'){
            steps{
                git branch: 'main', url: 'https://github.com/Jithesh-kumar/-jenkins-hello-world.git'
                sh "mvn clean package -DskipTests=true"
            }
        }
        stage('Unit Test'){
            steps{
                sh "mvn test"
                junit stdioRetention: '', testResults: 'target/surefire-reports/TEST-*.xml'
            }
        }
    }
}