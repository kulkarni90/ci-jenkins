#!/usr/bin/env groovy
pipeline {
    agent any
    tools {
            maven 'Maven 3.6.3' 
            jdk 'JAVA 1.8'
    }
    stages {
        stage('Build') {
            steps {
                echo 'maven clean'
                //ABC indicates the folder name where the pom.xml file resides
                sh ' mvn -f pom.xml clean install'  
                 }
          }
        stage('Unit Test') {
            steps {
                 sh 'mvn test'
                }
            }
		stage('Integration Test') {
            steps {
                  sh 'mvn verify -DskipUnitTests -Parq-wildfly-swarm '
                }
            }
        stage('Deploying build'){
            steps {
                sh 'mvn Deploy'
                }
	    }
      }	
}

