node
{
    def mavenhome = tool name:"maven3.6.3"
    stage('Checkoutcode')
    {
        git branch: 'development', credentialsId: 'bca4d123-67c8-4d68-9434-4f69194cdd55', url: 'https://github.com/LAVANYAlavanya14/maven-web-application.git'
    }
    stage('Build')
    {
        sh "${mavenhome}/bin/mvn clean package"
    }
    stage('ExecuteSonarqubereport')
    {
        sh "${mavenhome}/bin/mvn sonar:sonar"
    }
    stage('UploadartifactintoNexus')
    {
        sh "${mavenhome}/bin/mvn deploy"
    }
    stage('DeployintoTomcatserver')
    {
        sshagent(['b19f5c69-b475-4568-93c8-b998a46c4f34']) {
    // some block
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.59.107:/opt/apache-tomcat-9.0.41/webapps/"
}
    }
    
}
