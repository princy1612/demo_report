node
{
    stage('checkout')
    {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '01', url: 'https://github.com/princy1612/demo_report.git']]]) 
    }
    stage('testing')
    {
        bat 'javac BankAppln.java'
    }
      environment {
    GENERATE_REPORTS = 'true'
    }

   stage ('E2E')
  {
        sh """
        echo GENERATE_REPORTS is set to $GENERATE_REPORTS
          chmod +x ./Banktest.java
         bash -e ./Banktest.java
}
}
