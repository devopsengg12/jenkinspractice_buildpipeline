pipeline{
    agent any
	
    tools{
        jdk 'JAVA_HOME_JENKIN'
        maven 'MAVEN_HOME_JENKIN'
    }
    
        stages{
		      stage('checkout') {
            steps {
                // Get some code from a GitHub repository
                
				git 'https://github.com/devopsengg12/jenkinspractice_buildpipeline.git'

            }

           
        }
             stage('Compile'){
                
                steps{
                    sh 'mvn compile'
                }
                
            }
			
            stage('CodeReview'){
                
                steps{
                    sh 'mvn pmd:pmd'
                }
                //post{
				
                    //always{
                        //pmd pattern: 'target/pmd.xml'
                   // }
                //}
            }
			
			
            stage('UnitTest'){
                
                steps{
                    sh 'mvn test'
                }
                
                post {
                    always {
                       junit testResults: '**/target/surefire-reports/*.xml', allowEmptyResults: false
                }
            }
            }
            stage('MetriCheck'){
                
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
                
                steps{
                    sh 'mvn package'
                }
            }
			
			
			 stage('deploy'){
                
                steps{
                    echo 'mvn deploy do latter'
                }
            }
            
        }
    
    }
