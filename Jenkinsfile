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
          deploy adapters: [tomcat8(credentialsId: 'tomcat-user', path: '', url: 'http://ec2-54-208-62-204.compute-1.amazonaws.com:8080/')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
