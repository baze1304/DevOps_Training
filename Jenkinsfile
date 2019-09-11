#!/usr/bin/env groovy
import hudson.model.*
import java.net.URL

node{
	stage('Git Checkout'){
	    git 'https://github.com/baze1304/DevOpsClassCodes.git'
	}
	stage('Compile'){
	    withMaven(maven:'mymaven'){
	        sh 'mvn compile'
	    }
	}
	stage('Review'){
	    withMaven(maven:'mymaven'){
	        sh 'mvn pmd:pmd'
	    }
	}	
	stage('Test'){
		try {
			withMaven(maven:'mymaven'){
				sh 'mvn test'
			}
		} finally{
			junit 'target/surefire-reports/*.xml'
		}
	}
	stage('Coverage'){
		try {
			withMaven(maven:'mymaven'){
				sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
			}
		} finally{
			cobertura coberturaReportFile: 'target/coverage.xml'
		}}
	
	stage('Package'){
		withMaven(maven:'mymaven'){
	        sh 'mvn package'
	    }
	}
}
