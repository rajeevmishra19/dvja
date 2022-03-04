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

    stage ('OWASP Dependency-Check Vulnerabilities') 
	{

      steps 
	  {
        dependencyCheck additionalArguments: '', odcInstallation: 'ODC'
        dependencyCheckPublisher pattern: 'dependency-check-report.xml' 
        sh 'mv dependency-check-report.xml /var/jenkins_home/workspace/ODC_SCA/reports' 
      }
    }
		}
}
