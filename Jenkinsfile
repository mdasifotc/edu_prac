pipeline{
    tools{
        jdk 'Myjava'
        maven 'Mymaven'
    }
    agent any
    stages{
        stage('Checkout'){
            steps{
                git ''
            }
        }
        stage('compile'){
           
            steps{
                sh 'mvn compile'
            }
        }
        stage('codeReview'){
            steps{
                sh 'mvn pmd:pmd'
            }
     
        }
        stage('UnitTesting'){
           
            steps{
                sh 'mvn test'
            }
        }
        stage('metricCheck'){
            
            steps{
                sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
            }
      
        }
        stage('Package'){
            
            steps{
                sh 'mvn package'
            }
        }
    }
}
