pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/chaimakd/Front_Angular.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage("SonarQube Test"){
             agent any
                steps{
                   withSonarQubeEnv('sonar-server') {
                      sh 'mvn clean package sonar:sonar'
                     }
                   }
                }
    }
}
