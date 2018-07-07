#!/usr/bin/env groovy

def applicationName=''
def label=""
def mavenParameters= ''
def mavenGoals = ""
def mavenSettingXML = ''
def parentPom = ""



node ('master') {
	stage('SCM') {
	  def repoOwner = env.sourceRepositoryOwner
	  def repoName = env.sourceRepositoryName
	  def pullRequestID = env.pullRequestId
	  def branchName = env.BRANCH_NAME
	  //def workspacePath = $WORKSPACE
		
		echo "Repository Owner : $repoOwner"
		echo "Repository Name : $repoName"
		echo "Pull Request ID : $pullRequestID"
		echo "Branch Name : $branchName"
		//echo "Workspace : $workspacePath"
		
		
		properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '30', numToKeepStr: '30')), gitLabConnection(''), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'ThrottleJobProperty', categories: [], limitOneJobWithMatchingParams: false, maxConcurrentPerNode: 0, maxConcurrentTotal: 0, paramsToUseForLimit: '', throttleEnabled: false, throttleOption: 'project']])
		
	    ws('E:\\workspace\\jenkins\\Job2') {
	       //checkout([$class: 'GitSCM', branches: [[name: '*/integration/2018-JULY']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GITHubUser', url: 'https://github.com/keerthiraj86/India.git']]])
	        checkout scm
	        
	        echo "Executing maven build.."
	        withEnv(["JAVA_HOME=${ tool 'Windows-JAVA-1.8' }", "PATH+Maven=${tool 'Windows-Maven-3.5.4'}/bin:${env.JAVA_HOME}/bin"]) {
	            sh "mvn.cmd -f my-app/pom.xml clean install" 
	        }
	    }
	}
	
	stage ('Build Child Job') {
	    build job: 'ChildJob', parameters: [string(name: 'A', value: 'Apple')]
	}

}
