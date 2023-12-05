pipeline {
    agent { label 'MAVEN'}
    triggers {
        pollSCM('* * * * *')
    }
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
                    archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                    junit testResults: '**/TEST-*.xml'
                }
            }

        }
    
}