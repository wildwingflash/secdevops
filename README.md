
# So you want to be a SecDevOps???
This is the right place to start

![DEVSECOPS](/images/computer.png)

<!-- MarkdownTOC levels="0,1,2,3" autolink="true" -->

- [DevOps](#devops)
	- [Definition](#definition)
	- [Practices](#practices)
		- [Continuous Integration](#continuous-integration)
		- [Continuous Delivery / Continuous Deploy](#continuous-delivery--continuous-deploy)
		- [Microservices](#microservices)
		- [Infraestructure as Code](#infraestructure-as-code)
		- [Monitoring and Logging](#monitoring-and-logging)
		- [Comunication and Collaboration](#comunication-and-collaboration)
		- [Best practices](#best-practices)
- [SecDevOps](#secdevops)
	- [Definition](#definition-1)
	- [Practices](#practices-1)
		- [OWASP TESTING GUIDE 4.0](#owasp-testing-guide-40)
		- [SAST into CI/CD](#sast-into-cicd)
		- [DAST into CI/CD](#dast-into-cicd)

<!-- /MarkdownTOC -->

# DevOps

## Definition
https://aws.amazon.com/es/devops/what-is-devops/
In some DevOps models, quality assurance and security teams may also become more tightly integrated with development and operations and throughout the application lifecycle. When security is the focus of everyone on a DevOps team, this is sometimes referred to as DevSecOps.

https://www.atlassian.com/devops
DevOps is a set of practices that automates the processes between software development and IT teams, in order that they can build, test, and release software faster and more reliably. The concept of DevOps is founded on building a culture of collaboration between teams that historically functioned in relative siloes. The promised benefits include increased trust, faster software releases, ability to solve critical issues quickly, and better manage unplanned work

https://theagileadmin.com/what-is-devops/
DevOps is the practice of operations and development engineers participating together in the entire service lifecycle, from design through the development process to production support. 


## Practices

### Continuous Integration
https://www.thoughtworks.com/es/continuous-integration
Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early.
By integrating regularly, you can detect errors quickly, and locate them more easily.

https://www.atlassian.com/continuous-delivery/continuous-integration-intro
Continuous integration is the practice of routinely integrating code changes into the main branch of a repository, and testing the changes, as early and often as possible. Ideally, developers will integrate their code daily, if not multiple times a day.

https://codeship.com/continuous-integration-essentials
is the practice of integrating changes from different developers in the team into a mainline as early as possible, in best cases several times a day. This makes sure the code individual developers work on doesn’t divert too much. When you combine the process with automated testing, continuous integration can enable your code to be dependable.

https://aws.amazon.com/devops/continuous-integration/
Continuous integration is a DevOps software development practice where developers regularly merge their code changes into a central repository, after which automated builds and tests are run.

Tools: Jenkins (gitlab, github) , Travis (github)
Links to Code Review:
https://github.com/joho/awesome-code-review
https://github.com/mre/awesome-static-analysis

#### Comparison of CI
https://hackernoon.com/continuous-integration-circleci-vs-travis-ci-vs-jenkins-41a1c2bd95f5
https://blog.takipi.com/jenkins-vs-travis-ci-vs-circle-ci-vs-teamcity-vs-codeship-vs-gitlab-ci-vs-bamboo/
https://stackshare.io/stackups/jenkins-vs-travis-ci-vs-bamboo


### Continuous Delivery / Continuous Deploy
https://www.thoughtworks.com/es/continuous-delivery
Through reliable, low-risk releases, Continuous Delivery makes it possible to continuously adapt software in line with user feedback, shifts in the market and changes to business strategy. Test, support, development and operations work together as one delivery team to automate and streamline the build-test-release process.

https://www.atlassian.com/continuous-delivery/ci-vs-ci-vs-cd
Continuous delivery is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button.

Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

https://www.youtube.com/watch?v=hQ0recUXk9o

https://aws.amazon.com/devops/continuous-delivery/
Continuous delivery is a DevOps software development practice where code changes are automatically built, tested, and prepared for a release to production. It expands upon continuous integration by deploying all code changes to a testing environment and/or a production environment after the build stage. When continuous delivery is implemented properly, developers will always have a deployment-ready build artifact that has passed through a standardized test process.

https://puppet.com/blog/continuous-delivery-vs-continuous-deployment-what-s-diff
Continuous deployment is the next step of continuous delivery: Every change that passes the automated tests is deployed to production automatically. Continuous deployment should be the goal of most companies that are not constrained by regulatory or other requirements. 


Continuous Delivery Tools: Jenkins, travis, 
https://docs.travis-ci.com/user/deployment/releases/
https://cloud.google.com/solutions/continuous-delivery-with-travis-ci
https://stackify.com/top-continuous-integration-tools/
https://www.g2crowd.com/categories/continuous-integration
example workflows with jeninks
https://automatingguy.com/2017/11/06/jenkins-pipelines-simple-delivery-flow/
https://github.com/jjasghar/jenkinsfile_cookbook_pipeline


Continuous Deploy tools: ansible, vagrant, circleCI, chef, puppet, drone.io, octopus-deploy
https://medium.com/arabamlabs/blue-green-deployment-with-jenkins-98393bba2327
https://www.atlassian.com/blog/continuous-delivery/practical-continuous-deployment

### Microservices
### Infraestructure as Code
WAFs
F5
PT AF
imperva incapsula
akamai kona
cloudfare

BotManagers


### Monitoring and Logging
Airbrake: https://airbrake.io/

### Comunication and Collaboration


### Best practices
* train develpment teams to develop secure code
* track security issues the same as software issues
* If infraestructures i snow code, then security should be code
* Integrate security controls in the software pipeline
* Automate security test in the build process
* Detect know vulnerabilities duiring the pipeline
* Monitor security in production for known states
* Inject failure to ensure security is hardened
* https://docs.microsoft.com/en-us/azure/devops/


# SecDevOps

## Definition

## Practices

### OWASP TESTING GUIDE 4.0
Testing Techniques
* Manual Inspections & Reviews
* Threat Modeling (NIST 800-30)
* Source Code Review
* Penetration Testing

OWASP testing framework
![OWASPTestingFramework](/images/OWASP_Testing_Guide_v4.png)

Reporting
1. Project Objective
1. Project Scope
1. Project Schedule
1. Targets
1. Limitations
1. Findings Summary
1. Remediation Summary
1. Findings
	1. Screenshots & command lines
	1. the affected item
	1. technical description of the issue and the affected function
	1. resolving the issue
	1. severity rating [1], with vector tonation if using CVSS


### SAST into CI/CD
Source code analysis tools, also referred to as Static Application Security Testing (SAST) Tools, are designed to analyze source code and/or compiled versions of code to help find security flaws.
Important Selection Criteria

 * Requirement: Must support your programming language, but not usually a key factor once it does.
 * Types of vulnerabilities it can detect (out of the OWASP Top Ten?) (plus more?)
 * How accurate is it? False Positive/False Negative rates?
 *     Does the tool have an OWASP Benchmark score?
 * Does it understand the libraries/frameworks you use?
 * Does it require a fully buildable set of source?
 * Can it run against binaries instead of source?
 * Can it be integrated into the developer's IDE?
 * How hard is it to setup/use?
 * Can it be run continuously and automatically?
 * License cost for the tool. (Some are sold per user, per org, per app, per line of code analyzed. Consulting licenses are frequently different than end user licenses.)

Open source: bandit (python) https://github.com/PyCQA/bandit, findsecbugs https://find-sec-bugs.github.io/, google codesearchdiggity (not relevant), sonarqube https://www.sonarqube.org/features/integration/ seems promising!!

SonarQube issue workflow
Statuses
    Open - set by SonarQube on new issues
    Confirmed - set manually to indicate that the issue is valid
    Resolved - set manually to indicate that the next analysis should Close the issue
    Reopened - set automatically by SonarQube when a Resolved issue hasn't actually been corrected
    Closed - set automatically by SonarQube for automatically created issues. 

Resolutions
Closed issues will have one of two resolutions:
    Fixed - set automatically when a subsequent analysis shows that the issue has been corrected
    Removed - set automatically when either the related coding rule or the file is no longer available. The rule may not be available either because it has been removed from the profile or because the underlying plugin has been uninstalled. The file could be unavailable because it has been removed from the project, moved to a different location or renamed.

Resolved issues will have one of two resolutions:
    False Positive - set manually
    Won't Fix - set manually

There are open source solutions and also Commercial ones.
* https://github.com/PyCQA/bandit
* https://docs.gitlab.com/ee/user/project/merge_requests/sast.html
* https://www.checkmarx.com/2015/04/29/sast-vs-dast-why-sast-3/
* https://www.sourceclear.com/vulnerability-database/security/arbitrary-file-write/python/sid-6115/summary
* https://www.owasp.org/index.php/Source_Code_Analysis_Tools


benchmarking: https://rawgit.com/OWASP/Benchmark/master/scorecard/OWASP_Benchmark_Home.html


### DAST into CI/CD
Dynamic analysis seems much more complicated to be automated in case of Desktop Applications. 
We are talking about vulnerability scans, and automated ones. 

https://www.viva64.com/en/t/0070/
https://www.owasp.org/index.php/Category:Vulnerability_Scanning_Tools