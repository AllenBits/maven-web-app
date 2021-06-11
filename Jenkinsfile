node 
{
def mavenHome = tool name: 'Maven3.8.1'
stage('CodeClone') 
{
git credentialsId: 'git-credentials', url: 'https://github.com/AllenBits/web'
}
stage('mavenBuild')
{
sh "${mavenHome}/bin/mvn clean package"
}
 
//Groovy is a good lang
  
/*
Poll SCM trigger
*/

stage('DeployDocker')
{
sh "docker build -t image3 ."
sh "docker run -d -p 6000:8080 image3"
}
stage('emailnotification')
{
emailext body: '''Thank You
AllenBits''', recipientProviders: [developers()], subject: 'Job Status', to: 'femi4allen@yahoo.com'    
}     
 
 
  
/* 
stage('CodeQuality') 
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}
stage('UploadNexus')
{
sh "${mavenHome}/bin/mvn deploy"
}
stage('DeployTomcat')
{
deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://18.216.81.105:7000/')], contextPath: null, war: 'target/*war'
}
stage('emailnotification')
{
emailext body: '''Thank You
AllenBits''', recipientProviders: [developers()], subject: 'Job Status', to: 'femi4allen@yahoo.com'    
}    
 */
}
