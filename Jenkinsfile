#!/usr/bin/env groovy
import hudson.model.*
import java.net.URL

node{
	cleanWs()
	
	stage('Git Checkout'){
	    git 'https://github.com/baze1304/DevOpsClassCodes.git'
	}
	stage('Compile'){
		sh '${MAVEN_HOME}/mvn compile'	    
	}
	
	stage('Package'){
	       sh '${MAVEN_HOME}/mvn package'
	}
	stage('ssh'){
		sshagent (credentials: ['89ccc335-db06-4b8b-9b29-fc4932d4f8f3']) {
    		sh 'scp /var/lib/jenkins/workspace/parameter_pipeline/target/addressbook.war devopsuser@docker-2:/home/devopsuser'
  }
	}
}
