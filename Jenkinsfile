pipeline {
   agent any

   stages {
      stage('pull code') {
         steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '5cd539d5-8070-4437-9d2b-7f1dceb5bafa', url: 'https://github.com/jasonbai2014/Jenkins-Test.git']]])
         }
      }
      stage('build project') {
         steps {
            sh label: '', script: 'mvn clean package'
         }
      }
     stage('publish project') {
         steps {
            deploy adapters: [tomcat8(credentialsId: 'aa69bb6e-09c8-452d-8325-b1053c6a8a05', path: '', url: 'http://192.168.147.132:8080')], contextPath: null, war: 'target/*war'
         }
      }
   }
}
