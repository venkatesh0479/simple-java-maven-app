pipeline {
    agent any
        stages {
            stage('SCM checkout')
            {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'e8471536-0a33-454d-8d3d-5ac91298cb7d', url: 'https://github.com/venkatesh0479/simple-java-maven-app.git']]])
            }
        }
            stage('Build') 
{
                steps{
                    bat 'mvn clean package'
            }
            post{
                always{
                    junit 'target/surefire-reports/TEST-com*.xml'
                }
            }
        }
            stage('Email notification') 
{
                steps{
                    mail bcc: '', body: 'Hi, your java app has built and deployed to \'C:\\Users\\pc\\.jenkins\\workspace\\Java3\\target\'', 
                    cc: 'saimanojvarma.kutchrlapati@collins.com', from: '', replyTo: '', subject: 'Java Build Status',
                    to: 'venkatesh.gujjarlapudi@collins.com'
            }
        }
    }
}
