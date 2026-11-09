pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/Hrithik2230/Maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '8eedba60-aa26-4b27-a3a0-bf947eb826df', path: '', url: 'http://172.31.33.152:8080')], contextPath: 'test2', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/Hrithik2230/Testingcode.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline1/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
               deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '8eedba60-aa26-4b27-a3a0-bf947eb826df', path: '', url: 'http://172.31.46.104:8080')], contextPath: 'prod2', war: '**/*.war'
            }
        }
    }
}
