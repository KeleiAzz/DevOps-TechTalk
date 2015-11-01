##DevOps TechTalk - Snap CI
---
###Team Members:
* Kelei Gong
* Ying Huang
* Shanil Puri
* Shengpei Zhang

##Setup
###Add a repository
Login to [Snap CI](https://snap-ci.com/), GitHub will ask if you want to give a set of permissions to Snap. Snap will present a list of all the repositories you have access to, and then you can add a repository to Snap
###Configure the build steps
After adding the repository to Snap, it will clone the repository form Github to its cloud server, and then we can customize the build steps for this repository.

Snap will attempt to automatically detect some popular configurations for the build. It looks for languages versions, build tools files, dependency managers and other conventions that may indicate how the build could be set up.

For example, if we import a Rails project, it will get the language version and database type, then automatically create two steps for pipeline: FastFeedBack and Integration.

![image](pics/build-pipeline.png) 

In this example, it will run the basic setup for the Rails project, follows by unit test and functional test. We can customize this step by changing the commands to be executed, and add more stages to the pipeline. The stage trigger can be set to be either automatic or manual.  

Some additional settings like "Environment Variables" and "Secure Files" can give us more control over the building steps. And an important feature of Snap is that we can set the number of workers and the worker's size of this stage, thus it can run this stage in parallel or run multiple pipelines in parallel. One way of taking advantage of this is to run tests in parallel across multiple workers. And with larger size workers be useful in cases where the stage requires more memory to build.

![image](pics/additional-setting.png)

###Add a Deploy stage
Besides the building and testing parts in the pipeline, we can also add a Deploy stage, here we take deploy to Heroku as an example.

![image](pics/deploy.png)

The configuration is quite easy, it will redirect you to Heroku and ask for authorization, then choose an application name and check the perform DB migration if it's a production stage. At last, some "Heroku config vars" can be configured at will.

![image](pics/heroku.jpg)
##Reference
* https://docs.snap-ci.com/getting-started/