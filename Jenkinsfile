pipeline {
  agent any
  tools {
    maven 'maven-3.6.1'
  }
  stages {
    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Deploy to tomcat') {
      steps {
        sshagent(['tomcat']) {
          sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@52.90.52.15:/prod/apache-tomcat-8.5.81/webapps/webappT.war'
        }
      }
    }
  }
}
