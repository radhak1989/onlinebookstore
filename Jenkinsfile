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
                deploy adapters: [tomcat9(credentialsId: 'tomcatcred', path: '', url: 'http://18.219.141.253:8080')], contextPath: 'hook12', war: '**/*.war'
            }
        }
    }
}
