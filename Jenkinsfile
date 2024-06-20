pipeline {
    agent any

    stages {
        stage('clone from git') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/raghudeveloptrees/onlinebookstore.git'
            }
        }
        stage('build'){
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcatcred', path: '', url: 'http://34.227.73.213:8081')], contextPath: 'books', war: '**/*.war'
            }
        }
    }
}
