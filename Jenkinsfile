pipeline {
	agent any
		tools {
		maven 'M3'
		}
	stages{
		stage("Build"){
			steps{
				sh script: 'mvn clean package deploy'
			}
		}
		stage("Upload WAR to Nexus"){
			steps{
				nexusArtifactUploader artifacts: [
				    [
				    artifactId: 'simple-app', 
				    classifier: '', 
				    file: 'target/simple-app-3.0.0.war', 
				    type: 'war'
				    ]
			    ], 
			    credentialsId: 'nexus3', 
			    groupId: 'in.javahome', 
			    nexusUrl: '35.193.73.135:8081', 
			    nexusVersion: 'nexus3',
			    protocol: 'http', 
			    repository: 'simple-app', 
			    version: '3.0.0'
			}
		}
	}
}
