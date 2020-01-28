pipeline{
    tools{
        jdk 'Myjava'
        maven 'Mymaven'
    }
    agent any
    stages{

        stage('compile'){
            
            steps{
                sh 'mvn compile'
            }
        }
        stage('codeReview'){
           
            steps{
                sh 'mvn pmd:pmd'
            }
            post{
                always{
                    pmd pattern: 'target/pmd.xml'
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
            post{
                always{
                    cobertura coberturaReportFile: 'target/site/cobertura/coverage.xml'
                }
            }
        }
        stage('Package'){
            agent any
            steps{
                sh 'mvn package'
            }
        }
    }
}
