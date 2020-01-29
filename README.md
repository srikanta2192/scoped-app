# Introduction
This repo contains sample project structure for different types of scoped apps.

## example-scoped-app
This is a minimum structure of a scoped application. It doesn't need to use any of the JS tooling (preprocessors SASS, SCSS, transpilers, etc).

## example-spa-scoped-app
This is a more complex structure that utilizes modern JS tooling (webpack, gulp, npm, etc). You may need to adapt the `package.json` and `.builderc` for tectonic/seismic components.

## Latest versions
Both of the above examples use a parent pom to hide most of the complexity in a maven build. See [https://code.devsnc.com/dev/snc-parent-pom] for implementation details.

When you make copy of these projects, please make sure to use the latest parent version by running the following command in your new project:

	$ mvn versions:update-parent
	
	
	
### these are the options specificed the Maven release build.  you can override this options by specifying them	in your pom
	
	def opts = [
	    branchFilterIncludes: env.MULTIBRANCH_FILTER_INCLUDES ?: "paris orlando newyork madrid london kingston master secops-dev dev stable PR-* pr/* project/* story/* feature/*",
	    branchFilterExcludes: env.MULTIBRANCH_FILTER_EXCLUDES ?: "scratch/* release/* track/*",
	    dependencyScan: true,
	    dependencyPublish: true,
	    dependencyTopic: "SdlcAnalyzer",
	    dependencyNPMTopic: "SdlcScanDependencyResults",
	    dependencySeismicTopic: "SdlcSeismicDependencyResults",
	    enableRelease: true,
	    enableDeployTransfer: true,
	    releaseType: 'maven', // 'maven' or 'npm'
	    releaseFromGit: true,
	    releaseCommitPrefix: '[ci release]',
	    releaseTagFormat: 'release/@{project.artifactId}-@{project.version}',
	    ignoreTestFailures: true,
	    jdkVersion: 'JDK8',
	    mvnVerifyGoals: 'clean verify',
	    mvnBuildGoals: 'clean deploy',
	    mvnReleaseGoals: 'release:prepare release:perform',
	    mvnVersion: 'maven-3.6',
	    owners: '',
	    pom: env.MARKER_FILE ?: 'pom.xml',
	    slaveLabel: 'ci || dedicated-ci',
	    prBranches: 'update/.+',
	    debug: false,
	    downstreamJob: '',
	    githubCredentialsId: env.GITHUB_CODE_PUSH_CREDENTIALS ?: 'code_repo_push',
	    bt1CredentialsId: env.BT1_PUBLISHER_CREDENTIALS ?: 'bt1-publisher',
	    sauceCredentialsId: '',
	    xunitPattern: 'target/xunit-reports/**/*.xml,*/target/xunit-reports/**/*.xml,*/*/target/xunit-reports/**/*.xml',
	    deployPropertyPattern: 'target/snc-deploy.properties,*/target/snc-deploy.properties',
	    htmlReports: 'target/html-reports/**,target/xunit-reports/*.html',
	    releaseProgramID: '',
	    releaseProgramVersion: '',
	    splunkIncludes: 'target/splunk-reports/*.json',
	    splunkExcludes: '',
	    splunkFileSizeLimit: '100MB',
	    dependencyscanType: env.DEPENDENCY_SCAN_TYPE ?: 'npm',
	    publishNpmSnapshot: false
	  ]
