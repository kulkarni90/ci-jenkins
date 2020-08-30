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
                 sh 'maven test'
                }
            }
		stage('Integration Test') {
            steps {
                  sh 'maven verify -DskipUnitTests -Parq-wildfly-swarm '
                }
            }
        stage('Deploying build'){
            steps {
                sh 'maven Deploy'
                }
		}
    }	
            stage ('Post'){
                    steps { 
                        echo 'sent to mail'
                      }
                  }
             }
       }

