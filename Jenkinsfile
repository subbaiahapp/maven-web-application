node{
def mavenHome = tool name: 'maven3.8.5'
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '4', daysToKeepStr: '', numToKeepStr: '4')), pipelineTriggers([pollSCM('* * * * *')])])
 

//ckeck out the code 
stage('CheckoutCode'){
git branch: 'development', url: 'https://github.com/subbaiahapp/maven-web-application.git'

}
//build
stage('build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
//Execute sonarQube server
stage('ExecuteSonarQubeServer'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}


 //upload Artifacts into nexus
stage('uploadArtifactsintoNexus'){
sh "${mavenHome}/bin/mvn deploy"
}

//deploy app in tomcat
stage('Deploy App'){
sshagent(['a21cb3de-2285-4358-a13d-4352261a2c2b']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.5.92:/opt/apache-tomcat-9.0.68/webapps/"
}
}
*/
    

}//node closing
