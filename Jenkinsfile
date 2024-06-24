pipeline {
    agent any

    stages {
        stage('git') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/gsreddy1870/jpetstore-6.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'd198ccb7-cf3e-47a2-8276-07285eccf2c5', path: '', url: 'http://16.171.238.128:8080')], contextPath: pets, war: '**/*.war'
            }
        }
    }
}
