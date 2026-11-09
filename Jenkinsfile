node('built-in')
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
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '8eedba60-aa26-4b27-a3a0-bf947eb826df', path: '', url: 'http://172.31.33.152:8080')], contextPath: 'test1', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/Hrithik2230/Testingcode.git'
        sh 'java -jar /var/lib/jenkins/workspace/Scriptedpipeline1/testing.jar'
    }
    stage('ContinuousDelivery')
    {
       deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '8eedba60-aa26-4b27-a3a0-bf947eb826df', path: '', url: 'http://172.31.46.104:8080')], contextPath: 'prod1', war: '**/*.war'
    }
}
