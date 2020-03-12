pipeline {
    libraries{
    lib 'shlib'
    }
    agent any
    tools {
        maven "Maven"   
    }   
    environment{
        sonarscanner = tool 'SonarScanner'
    }
    stages {
        stage('Compile-Build-Test ') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis'){
            steps{
               withSonarQubeEnv('sonarqube'){
                     sh '${sonarscanner}/bin/sonar-scanner -Dproject.settings=./sonar-project.properties'
                }
            }
        }
    }
}
