pipeline{
    agent any
    stages{
        stage('Checkout SCM'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/itaifrenkel/java-hello-world-webapp.git']]])
            }
        }    
        stage('Build'){
            steps{
                sh 'mvn clean install'
                sh "ls -al target"
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Code Quality'){
            steps{
                withSonarQubeEnv(credentialsId: 'sonar-token',installationName: 'Sonar'){
                sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Jaccoco Report'){
            steps{
                jacoco exclusionPattern: '**/src/main/java', inclusionPattern: '**/*.class'
            }
        }
        stage('Tomcat Deploy'){
            steps{
                sh "ls -al"
                sh """cp 'target/java-hello-world.war' /c/Users/raval/Downloads/apache-tomcat-9.0.27/apache-tomcat-9.0.27/webapps"""
            }
        }
