pipeline{
    tools{
        jdk 'Myjava'
        maven 'Mymaven'
    }
    agent any
    stages{
        stage('Checkout'){
            steps{
                git 'https://github.com/mdasifotc/edu_prac.git'
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
            post { 
                always
            {
            pmd pattern : 'target/pmd.xml'
            }
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
            post {
                always {
                  
                }
            }
        }
        stage('Package'){
            
            steps{
                sh 'mvn package'
            }
        }
    }
}
