## Prerequsite

* Minikube v1.6.2 or greater

* Docker 19.03 or greater

* Git 2.28 or greater

## Questions

1. What is git flow and its variations?  
A:  
	It is a branching model for Git, created by Vincent Driessen. It has attracted a lot of attention because it is very well suited to collaboration and scaling the development team.
	One of the great things about GitFlow is that it makes parallel development very easy, by isolating new development from finished work. New development (such as features and non-emergency bug fixes) is done in feature branches, and is only merged back into main body of code when the developer(s) is happy that the code is ready for release.
	Although interruptions are a BadThing(tm), if you are asked to switch from one task to another, all you need to do is commit your changes and then create a new feature branch for your new task. When that task is done, just checkout your original feature branch and you can continue where you left off.
	Feature branches also make it easier for two or more developers to collaborate on the same feature, because each feature branch is a sandbox where the only changes are the changes necessary to get the new feature working. That makes it very easy to see and follow what each collaborator is doing.
	As new development is completed, it gets merged back into the develop branch, which is a staging area for all completed features that haven’t yet been released. So when the next release is branched off of develop, it will automatically contain all of the new stuff that has been finished.
	GitFlow supports hotfix branches - branches made from a tagged release. You can use these to make an emergency change, safe in the knowledge that the hotfix will only contain your emergency fix. There’s no risk that you’ll accidentally merge in new development at the same time.
	Another popular branching model is Github flow which suits better for small and frequently updated projects.

2. What is Continuous integration ?  
A:  
	In software engineering, continuous integration (CI) is the practice of merging all developers' working copies to a shared mainline several times a day.
	When embarking on a change, a developer takes a copy of the current code base on which to work. As other developers submit changed code to the source code repository, this copy gradually ceases to reflect the repository code. Not only can the existing code base change, but new code can be added as well as new libraries, and other resources that create dependencies, and potential conflicts.
	The longer development continues on a branch without merging back to the mainline, the greater the risk of multiple integration conflicts[4] and failures when the developer branch is eventually merged back. When developers submit code to the repository they must first update their code to reflect the changes in the repository since they took their copy. The more changes the repository contains, the more work developers must do before submitting their own changes.
	Eventually, the repository may become so different from the developers' baselines that they enter what is sometimes referred to as "merge hell", or "integration hell",[5] where the time it takes to integrate exceeds the time it took to make their original changes.  

	Continuous integration (CI) is a software development strategy that increases the speed of development while ensuring the quality of the code that teams deploy. Developers continually commit code in small increments (at least daily, or even several times a day), which is then automatically built and tested before it is merged with the shared repository.  
	
	Continuous integration overview:  
	    Every developer commits daily, or even more often, to a shared mainline code repository  
	    Every commit triggers an automated build and test of the codebase  
	    If the build or any test fails, it’s repaired quickly – often within minutes  

	Continuous integration works hand-in-hand with Agile methodologies. Team members work on incremental “stories” and the code for these software changes is merged incrementally into the shared software repository multiple times a day.  

	Continuous integration is the automated building and testing of your application on every new commit.  


3. What is Continuous deployment?  
A:  
	It is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time and, when releasing the software, doing so manually.[1][2] It aims at building, testing, and releasing software with greater speed and frequency. The approach helps reduce the cost, time, and risk of delivering changes by allowing for more incremental updates to applications in production. A straightforward and repeatable deployment process is important for continuous delivery.
	CD contrasts with continuous deployment, a similar approach in which software is also produced in short cycles but through automated deployments rather than manual ones. 
	Continuous delivery and DevOps are similar in their meanings and are often conflated, but they are two different concepts.[3] DevOps has a broader scope,[4] and centers around the cultural change, specifically the collaboration of the various teams involved in software delivery (developers, operations, quality assurance, management, etc.), as well as automating the processes in software delivery.[4] Continuous delivery, on the other hand, is an approach to automate the delivery aspect, and focuses on bringing together different processes and executing them more quickly and more frequently.[5] Thus, DevOps can be a product of continuous delivery, and CD flows directly into DevOps.

	Continuous delivery is a state where your application is always ready to be deployed. A manual step is required to actually deploy the application.
	Continious deployment is like a continious delivery but with an automatic deployment without manual approval.
	The automation of building, testing, and deploying. If all tests pass, every new commit will push new code through the entire development pipeline to production with no manual intervention.

4. What types of deployment can you name and describe ? (Green-blue, etc.)  
A:  
	Recreate: Version A is terminated then version B is rolled out.  
	Ramped (also known as rolling-update or incremental): Version B is slowly rolled out and replacing version A.  
	Blue/Green: Version B is released alongside version A, then the traffic is switched to version B.  
	Canary: Version B is released to a subset of users, then proceed to a full rollout.  
	A/B testing: Version B is released to a subset of users under specific condition.  
	Shadow: Version B receives real-world traffic alongside version A and doesn’t impact the response.  


5. What types of testing do you know? What are they?  
A:  

    Functional Testing types include:  
	    Unit Testing  
	    Integration Testing  
	    System Testing  
	    Sanity Testing  
	    Smoke Testing  
	    Interface Testing  
	    Regression Testing  
	    Beta/Acceptance Testing  

	Non-functional Testing types include:  
	    Performance Testing  
	    Load Testing  
	    Stress Testing  
	    Volume Testing  
	    Security Testing  
	    Compatibility Testing  
	    Install Testing  
	    Recovery Testing  
	    Reliability Testing  
	    Usability Testing  
	    Compliance Testing  
	    Localization Testing  

	The meaning of each test can be read at: https://www.softwaretestinghelp.com/types-of-software-testing/  


6. `*` Describe how the code from the developer's computer reaches the production environment? What stages would you set up?  
A:

	Developer's local PC environment from which the developer pushes his code into his own feature branch on CI server repository.  
	CI environment with a shared GIT repository, it may run Jenkins, Gitlab, etc.  
	Test environment executes required unit tests  
	PR merges development branch after tests passed successfully  
	Development branch is deployed into staging environment for running more tests like regression tests, etc.  
	Development branch is being merged with release branch, deployed to prod2 and more tests are run  
	Prod2 environment can be used for testing with a subsets of production users in deployment strategies like Canary, A/B, etc.  
	Prod environment is a final target for all production users  

## Tasks

* Log in to https://circleci.com/ with your github account 

* Edit `.circleci/config.yaml` and create pipelines that:
    * build your [dockerfile](../02%20-%20dockerfile/Dockerfile) with new version tag and store in into a registry (dockerhub or smth else with public access)

    *  `*` update your [docker-compose](../03%20-%20docker-compose/example/docker-compose.yaml) with a new tag and create new release with changelog

    *  `*` update you helm charts and umbrella helm chart, create release in your repository, download release and redeploy umbrella helm chart to minikube for testing

A:  
	Please use the latest build of the image from:
	https://hub.docker.com/r/aprokopyev/provectus/tags?page=1&ordering=last_updated

	![Screenshot of the results](https://raw.githubusercontent.com/aprokopyev/internship/main/devops/05%20-%20ci-cd/provectus_ci.jpg)