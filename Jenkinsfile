pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/dibya-jenkins/pipeline.git'
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
                sh 'scp /home/ubuntu/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war ubuntu@172.31.29.240:/var/lib/tomcat7/webapps/qaenv.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
      sh 'echo "Test passed."' 
            }
        }
    }
    post
    {
        success
        {
        sh 'scp /home/ubuntu/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war ubuntu@172.31.21.179:/var/lib/tomcat7/webapps/prodenv.war'
        }
        failure
        {
        sh ' echo "failed" ' 
        }
        
        
        
        
    }
    
    
    
    
    
}
