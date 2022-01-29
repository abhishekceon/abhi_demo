pipeline {
    agent {label "test-label"}

    tools {
        maven "maven-3.6.3"
    }

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/abhishekceon/abhi_demo.git'
                sh "mvn -Dmaven.test.failure.ignore=true -s settings.xml clean install"
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
