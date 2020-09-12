#!groovy


import groovy.json.*


def SERVICE_NAME = 'madelyn-test'
def BRANCH_NAME = "${env.BRANCH_NAME}".replaceFirst(/^release\//){''}
def TAG = "${BRANCH_NAME}_${env.BUILD_NUMBER}"
def IMAGE_NAME = "${SERVICE_NAME}:${TAG}-E2E"


pipeline {
  agent {
 }
   triggers {
    cron('H 0 * * *')
   }
options {
    //ansiColor('xterm')
    buildDiscarder(logRotator(numToKeepStr: '5', artifactDaysToKeepStr: '10'))
    //timestamps()
}
    stages {
        stage('checkout'){
            steps
       
  {
     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '01', url: 'https://github.com/princy1612/demo_report.git']]]) 
  }
    environment {
    GENERATE_REPORTS = 'true'
    }
 stages {
   stage ('E2E') {
      steps {
        sh """
        echo GENERATE_REPORTS is set to $GENERATE_REPORTS
          chmod +x ./Banktest.java
         bash -e ./Banktest.java
        """
      }
   }
  }
}





//node
{
//    stage('checkout')
 //   {
  //     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '01', url: 'https://github.com/princy1612/demo_report.git']]]) 
  //  }
  //  stage('testing')
 //   {
  //      bat 'javac BankAppln.java'
  //  }
  //    environment {
  //  GENERATE_REPORTS = 'true'
  //  }

 //  stage ('E2E')
 // {
   //     sh """
      //  echo GENERATE_REPORTS is set to $GENERATE_REPORTS
     //     chmod +x ./Banktest.java
     //    bash -e ./Banktest.java
}//
}//
