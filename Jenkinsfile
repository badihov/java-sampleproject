pipeline {
  agent any
  tools {
    maven 'Maven' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat8(credentialsId: 'tomcat-users', path: '', url: 'http://http://ec2-44-208-163-155.compute-1.amazonaws.com:8080/')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
