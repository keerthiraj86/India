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
	  def workspacePath = $WORKSPACE
		
		echo "Repository Owner : $repoOwner"
		echo "Repository Name : $repoName"
		echo "Pull Request ID : $pullRequestID"
		echo "Branch Name : $branchName"
		echo "Workspace : $WORKSPACE"
		
	  //checkout([$class: 'GitSCM', branches: [[name: '*/integration/2018-JULY']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GITHubUser', url: 'https://github.com/keerthiraj86/India.git']]])
	  checkout scm
	}

}
