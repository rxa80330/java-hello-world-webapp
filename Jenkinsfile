@Library('jenkins-shared-library@master') 
def call(Map stageParams) {
pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
            javapipeline(
                branch: "master",
                url: "https://github.com/rxa80330/java-hello-world-webapp.git"
            )
            }
    }
    }
}
}
