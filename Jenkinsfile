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
                deploy adapters: [tomcat9(credentialsId: 'tomcatcred', path: '', url: 'http://52.91.71.175:8090')], contextPath: 'bookstore', war: '**/*.war'
            }
        }
    }
}
