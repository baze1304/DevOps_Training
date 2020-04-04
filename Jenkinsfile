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
}
