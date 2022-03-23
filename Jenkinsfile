
Pipeline
{
  agent any
  tools 
  {
    jdk 'JDK 9.0'
    maven 'mvn-3.8.4'
  }

  stages 
	{
	stage ('SCA') 
	{  
    steps 
	{  
     withMaven(maven : 'mvn-3.8.4') 
	 {  
     	  synopsys_detect detectProperties: '--blackduck.url=https://poc93.blackduck.synopsys.com --blackduck.api.token=MDBlMzUyOWMtZjBiYy00NTVlLThkNjQtOGE5OGY5ZWJiNmQzOjA1NDhhY2YxLTliMzEtNGQ1Ni1iMDhlLWU5N2NiYjlhZTYyMg== --detect.impact.analysis.enabled=true --detect.project.name=dvja --detect.risk.report.pdf=true --detect.risk.report.pdf.path=/var/jenkins_home/workspace/SCA_Synopsys_DVJA/ --detect.project.version.name=1.6 --blackduck.trust.cert=true --detect.maven.path=/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/mvn-3.8.4/bin/mvn --detect.maven.build.command=clean package', downloadStrategyOverride: [$class: 'AirGapDownloadStrategy', airGapInstallationName: 'AirGAP']
     }  
   
     dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'  
    }  
   }  
		}
}
