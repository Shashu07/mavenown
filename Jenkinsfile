pipeline
{
    agent any
    stages
    {
        stage('ContinuosDownload')
        {
            steps
           {
               script
               {
                try
                {
                     git 'https://github.com/intelliqittrainings/maven.git'
                }
                catch(Exception e1)
                {
                    mail bcc: '', body: 'jenkins is unable to download the dev code from git repo', cc: '', from: '', replyTo: '', subject: 'Downloads failed', to: 'git admin@gmail.com'
                    exit(1)
                     }
               }
           }
        }
        stage('ContinuosBuild')
        {
            steps
           {
               script
               {
               try
               {
                   sh 'mvn package'
               }
               catch(Exception e2)
               {
                   mail bcc: '', body: 'jenkins is unable to build an artifact form the code', cc: '', from: '', replyTo: '', subject: 'build failed', to: 'developres@gmail.com'
               }
               }
           }
        }
        stage('ContinuoDeployment')
        {
            steps
           {
               script
               {
               try
               {
                   deploy adapters: [tomcat9(credentialsId: '717abc9d-5f04-4862-b7c0-3783d63dfd3a', path: '', url: 'http://172.31.24.84:8080')], contextPath: 'qaapp', war: '**/*.war'
               }
               catch(Exception e3)
               {
                   mail bcc: '', body: 'jenkins is unable to deploy into tomcat ont he qaserver', cc: '', from: '', replyTo: '', subject: 'deploymentfailed', to: 'middleware@gmail.com'
               }
               }
           }
        }
         stage('Continuostesting')
        {
            steps
           {
               script
               {
               try
               {
                    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline1/testing.jar'
               }
               catch(Exception e4)
               {
                   mail bcc: '', body: 'functional tettins ad failed', cc: '', from: '', replyTo: '', subject: 'testing failed', to: 'middleware@gmail.com'
                   exit(1)
               }
               }
           }
        }
         stage('ContinuousDelivey')
         {
             steps
             {
                 script
                 {
                 try
                 {
                     deploy adapters: [tomcat9(credentialsId: '717abc9d-5f04-4862-b7c0-3783d63dfd3a', path: '', url: 'http://172.31.26.222:8080')], contextPath: 'prodapp', war: '**/*.war'
                 }
                 catch(Exception e5)
                 {
                     mail bcc: '', body: 'jenkins is unable to deploy into tomcat on the prodserver', cc: '', from: '', replyTo: '', subject: 'deploymantfailed', to: 'deployment@gmail.com'
                 }
                 }
             }
         }
    }
   
    }
    
    
    

