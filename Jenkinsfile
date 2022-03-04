pipeline 
{
  agent any

  tools 
  {
    jdk 'JDK 9.0'
    maven 'mvn-3.8.4'
  }

  stages 
		{
    stage('Build') 
	{
      steps 
		{
        withMaven(maven : 'mvn-3.8.4') 
			{
          sh "mvn clean package"
			}      
		}
    }

stage ('OWASP Dependency-Check Vulnerabilities') {  
    steps {  
     withMaven(maven : 'mvn-3.6.3') {  
      sh 'mvn dependency-check:check'  
     }  
   
     dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'  
    }  
   }  
		}
}
