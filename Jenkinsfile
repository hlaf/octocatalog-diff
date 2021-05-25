#!groovy

@Library('emt-pipeline-lib@master') _

repo_creds   = 'emt-jenkins-github-ssh'
domain_name  = getDnsDomainName()
artifact_repo_url = "http://nexus.${domain_name}:8082/repository/emt-gems-internal/"
artifact_repo_creds = 'nexus-credentials'
build_tools_image = 'ruby:2.7.0'

node('docker-slave') {

  stage('commit.checkout') {
	checkout(scm)
  }

  stage('commit.assemble') {
    sh """docker run -t --volumes-from $DOCKER_CONTAINER_ID -w ${env.WORKSPACE} $build_tools_image \
      /bin/sh -c 'gem build *.gemspec'
    """
  }

  stage('release') {
//    withCredentials([usernameColonPassword(
//			credentialsId: artifact_repo_creds,
//			variable: 'NEXUS_CREDENTIALS')]) {
//
//		    sh """docker run -t --volumes-from $DOCKER_CONTAINER_ID -w ${env.WORKSPACE} $build_tools_image \
//              /bin/sh -c "gem install nexus && \
//                          gem nexus --url ${artifact_repo_url} --credential \${NEXUS_CREDENTIALS} *.gem"
//            """
//	}
  }

}
