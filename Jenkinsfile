pipeline {
    agent { label 'MAVEN'}
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
                }
            }

        }
    
}