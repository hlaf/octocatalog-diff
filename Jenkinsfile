#!groovy

@Library('emt-pipeline-lib@master') _

repo_creds   = 'emt-jenkins-github-ssh'
domain_name  = getDnsDomainName()
artifact_repo_url = "http://nexus.${domain_name}:8082/repository/emt-gems-internal/"
artifact_repo_creds = 'nexus-credentials'

node('docker-slave') {

  stage('Checkout') {
	checkout(scm)
  }

  stage('Release') {
	uploadToArtifactRepository(artifact_repo_url, artifact_repo_creds)
  }
}
