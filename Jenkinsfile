#!/usr/bin/env groovy
import hudson.model.*
import hudson.EnvVars
import java.net.URL

node{
    stage('connect to github'){
        git 'https://github.com/edureka-git/DevOpsClassCodes.git'
    }
    stage('Compile addressbook'){
        withMaven(Maven :'MyMaven'){
            sh 'mvn compile'
        }
    }
    stage('Code Reveiw'){
        withMaven(Maven:'MyMaven'){
            sh 'mvn pmd:pmd'
        }
    }
    stage('pmd publisher'){
        pmd canComputeNew: false, 
        defaultEncoding: '',
        healthy: '',
        pattern: 'target/pmd.xml',
        unHealthy: ''
    }
    stage('Package'){
        withMaven(Maven :'MyMaven'){
            sh 'mvn package'
        }
                
    }
}
