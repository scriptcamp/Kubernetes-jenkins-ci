podTemplate(containers: [
    containerTemplate(
        name: 'maven', 
        image: 'maven:3.8.1-jdk-8', 
        command: 'sleep', 
        args: '30d'
        ),
    containerTemplate(
        name: 'python', 
        image: 'python:latest', 
        command: 'sleep', 
        args: '30d')
  ]) {

    node(POD_LABEL) {
        stage('Get a Maven project') {
            git 'https://github.com/spring-projects/spring-petclinic.git'
            container('maven') {
                stage('Build a Maven project') {
                    sh '''
                    echo "maven build"
                    '''
                }
            }
        }

        stage('Get a Python Project') {
            git url: 'https://github.com/hashicorp/terraform.git', branch: 'main'
            container('python') {
                stage('Build a Go project') {
                    sh '''
                    echo "Go Build"
                    '''
                }
            }
        }

    }
}
