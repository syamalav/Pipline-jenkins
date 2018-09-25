
node('master') 
{
    stage('ContinuousDownload-Feature1') 
    {
        git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild-Feature1') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment-Feature1') 
    {
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.32:/var/lib/tomcat7/webapps/qaenv.war'
    }
    stage('ContinuousTesting-Feature1') 
    {
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
       sh 'java -jar /home/vagrant/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    
    stage('ContinuousDelivery-Feature1')
    {
        input message: 'Waiting for approval', submitter: 'Venu'
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.33:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
   
   
   
   
   
   
}
