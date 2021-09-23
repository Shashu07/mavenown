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
    }
   
    }
    
    
    

