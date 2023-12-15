pipeline {
    agent any   
        stages {
            stage('git') {
                steps {
                    git url: 'https://github.com/neelimaanagani/spring-petclinic-dummy.git',
                    branch: 'dev'           
                }
            }
            stage('build') {
                steps {
                    sh 'mvn --version'
                    sh 'mvn clean package'  
                    withSonarQubeEnv(installationName : 'SONAR_CLOUD',credentialsId: 'SONAR_CLOUD') {
                        sh 'mvn clean verify sonar:sonar -Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=jenkins-sonarnew -Dsonar.projectKey=jenkins-sonarnew_sonar-cloud'
                    }
                }
            
            
            post {
                success {
                    archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                    junit testResults: '**/TEST-*.xml'
                }
                failure {
                    mail body: 'Check the script', from: 'neelima.anagani@gmail.com', subject: 'Build failed', to: 'neelima.anagani@gmail.com'
                }
            }
            }

        }
    
}