pipeline {
    agent { label 'POLL'}
    triggers {
        cron('30 7 * * 1-5')
    }
        stages {
            stage('git') {
                steps {
                    git url: 'https://github.com/neelimaanagani/spring-petclinic-dummy.git',
                    branch: 'release'                    
                }
            }
            stage('build') {
                steps {
                    sh 'mvn --version'
                    sh 'mvn clean package'                    
                }
            }
            stage('post') {
                steps {
                    archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                    junit testResults: '**/TEST-*.xml'
                }
            }

        }
    
}