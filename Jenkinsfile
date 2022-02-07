node('master')
{
    def mavenHome= tool name: "maven-3.8.4"  //Name should be same as global tool configuration maven name.
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
  stage('Checkout the code'){
      git branch: 'development', credentialsId: '59427ccc-238e-4baa-b2dc-b48708d1dc85', url: 'https://github.com/rameshkpit1/maven-web-application.git'
  }
  stage('Build'){
     
      sh "${mavenHome}/bin/mvn clean package"
  }
 
  stage('ExecuteSonarReport'){
    sh "${mavenHome}/bin/mvn sonar:sonar"
  }
    /*
  stage("Quality Gate"){
    timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
    def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
    if (qg.status != 'OK') {
        error "Pipeline aborted due to quality gate failure: ${qg.status}"
    }else{
        print "Pipeline quality gate status: ${qg.status}"
    }
  }
}
 
  stage('UploadArtifactsIntoNexus'){
      sh "${mavenHome}/bin/mvn deploy"
  }
  */
}
