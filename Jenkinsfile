node 
{
    stage('ContinuousDownload') 
    {
       git 'https://github.com/Hrithik2230/Maven.git'
    }
    stage('ContinuousBuild') 
    {
       sh 'mvn package'
    }
    stage('ContinuousDeployment') 
    {
       deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '2b37dc73-7c57-4a83-b72e-1ef37b7e09ca', path: '', url: 'http://172.31.34.229:8080')], contextPath: 'Testapp', war: '**/*.war'
    }
     stage('ContinuousTesting') 
    {
       git 'https://github.com/Hrithik2230/Testingcode.git'
       sh 'java -jar /home/ubuntu/.jenkins/workspace/Scriptedpipeline1@2/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
       deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '2b37dc73-7c57-4a83-b72e-1ef37b7e09ca', path: '', url: 'http://172.31.33.192:8080')], contextPath: 'Liveapp', war: '**/*.war'
    }
}

