#!groovy

@Library('emt-pipeline-lib@master') _

repo_creds   = 'emt-jenkins-github-ssh'
domain_name  = getDnsDomainName()
artifact_repo_url = "http://nexus.${domain_name}:8082/repository/emt-gems-internal/"
artifact_repo_creds = 'nexus-credentials'

node('linux') {

  stage('commit.checkout') {
	checkout(scm)
  }

  stage('commit.assemble') {

    sh '''#!/bin/bash -l
	shopt -s expand_aliases # required by the bundle command on Windows

	module load rvm
	rvm use 2.3.8
    gem build *.gemspec
    '''

  }
  
  stage('release') {
	uploadToArtifactRepository(artifact_repo_url, artifact_repo_creds)
  }

}
