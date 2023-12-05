pipeline {
    agent { label 'MAVEN'}
        stages {
            stage('git') {
                steps {
                    git url: 'https://github.com/neelimaanagani/spring-petclinic-dummy.git'
                    sh 'mvn --version'
                }
            }

        }
    
}