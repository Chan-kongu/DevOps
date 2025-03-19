pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'main', url: 'https://github.com/anto096/simple-web-app.git'
            }
        }
        stage('build') {
            steps {
               bat "mvn clean"
               bat "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  bat 'docker build -t demohub/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                  bat 'docker push demohub/simplewebapp'
               }
            }
            }
}
}
}
