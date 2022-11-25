pipeline{

agent any
tools {
  maven 'maven3.8.5'
}properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])
  
 

stages{
stage('CheckoutCode'){
steps{
git branch: 'development', url: 'https://github.com/subbaiahapp/maven-web-application.git'
}
}
stage('build'){
steps{
sh "mvn clean package"
}
}
stage('sonarqube'){
steps{
sh"mvn clean sonar:sonar"
}
}

stage('nexus repository'){
steps{
sh "mvn clean deploy"
}
}

stage('tomcat deploy'){
steps{
sshagent(['a21cb3de-2285-4358-a13d-4352261a2c2b']){
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.5.92:/opt/apache-tomcat-9.0.68/webapps/"
}
}
}




}//stages closing
}//pipeline closing
