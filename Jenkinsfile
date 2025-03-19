pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'main', url: 'https://github.com/Chan-kongu/DevOps.git'
            }
        }
        stage('build') {
            steps {
               sh "mvn clean"
               sh "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  sh 'docker build -t demohub/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                  sh 'docker push demohub/simplewebapp'
               }
            }
            }
}
}
}
