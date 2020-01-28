pipeline 
{
    tools 
    {
        jdk 'myjava'
        maven 'mymaven'
        
    }
    agent any
    stages
    {
        stage('checkout') 
        {
            steps
            {
                git 'https://github.com/mdasifotc/edu_prac.git'
            }
            
        }
            stage('compile')
            {
                steps
                {
                    sh 'mvn compile'
                }
                
            }
            stage('codeReview')
          {
            steps
            {
             sh 'mvn pmd:pmd'    
            }
            
           }  
         stage ('UnitTesting')
         {
             steps
             {
                 sh 'mvn test'
             }
             
         }
        stage('metricCheck')
            {
        steps 
        {
            sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
        }
            
        }
    stage ('Package')
    {
        steps
        {
            sh 'mvn package'
        }
    }
        
    }
    
        
        
    }
    
    
