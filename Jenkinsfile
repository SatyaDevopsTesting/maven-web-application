node{
     def mavenHome = tool name: "maven"
     properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
  
    stage('checkoutCode'){
      git branch: 'development', credentialsId: 'ca275210-41e6-474e-9d15-037bbf8ec35d', url: 'https://github.com/SatyaDevopsTesting/maven-web-application.git'
    }
    stage('build'){
        sh "${mavenHome}/bin/mvn clean package"
    }
     //stage('ExecutingSonarQubereport'){
     //   sh "${mavenHome}/bin/mvn sonar:sonar"
  //  }
  //  stage('DeployArtifactintoNexus'){
  //      sh "${mavenHome}/bin/mvn deploy"
  //  }
//    stage('DeployappintoTomcatServer'){
 //   sshagent(['cdea29e3-b368-4e74-9a28-488d8f31b7a5']) {
 //   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.110.213.18:/opt/apache-tomcat-10.0.16/webapps/"
//}
// }
    stage('EmailNotification'){
        emailext body: '''Build is over!!

Regards
satya praveen''', subject: 'Build is over', to: 'satyapraveen22@gmail.com'
    }

 }
