node('built-in') 
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/sudarshansw7/mymaven.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'ee38dee2-e7f9-4d51-9c20-2b4cb296a741', path: '', url: 'http://172.31.14.89:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/sudarshansw7/myfunctionaltesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline2/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'ee38dee2-e7f9-4d51-9c20-2b4cb296a741', path: '', url: 'http://172.31.11.60:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
