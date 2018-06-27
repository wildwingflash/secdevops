
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
train develpment teams to develop secure code
track security issues the same as software issues
If infraestructures i snow code, then security should be code
Integrate security controls in the software pipeline
Automate security test in the build process
Detect know vulnerabilities duiring the pipeline
Monitor security in production for known states
Inject failure to ensure security is hardened


# SecDevOps

## Definition

## Practices
