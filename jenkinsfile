node{
    
    def mavenHome = tool name: "maven3"
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    stage('CheckOutCode')
    {
        git branch: 'development', credentialsId: '66d98407-6f16-4ebe-b918-59e2ff99dab9', url: 'https://github.com/ypr27/maven-web-application.git'
    }
    stage('BuildProjectintoMaven')
    {
        sh "${mavenHome}/bin/mvn clean package"
    }
   /* stage('ExecuteSonarQubeReport')
    {
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    stage('UploadArtifactsintoNexus')
    {
        sh "${mavenHome}/bin/mvn deploy"
    }
    stage('DeployProjectintoTomcat')
    {
       sshagent(['2347cf56-6253-4deb-9bc5-2e0a296f4cb9']) {
        sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.244.42:/opt/apache-tomcat-9.0.50/webapps"
    }
    } */
    stage('EmailNotification')
    {
        emailext body: '''Regards,
     prathap''', subject: 'Build Over', to: 'yannamprathap@gmail.com'
    }
}
