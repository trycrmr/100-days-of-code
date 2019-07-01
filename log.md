# Terry's 100 Days Of Code - Log

### [Day 61](#day-61)
#### July 1st, 2019
**Today's Progress**: 
- Iterate over latest CloudFormation template, debugging whatever issues arise

**Thoughts:** Debugging day successful! Learned lots about iterating over CloudFormation templates.

It turns out the stack I was attempting to deploy was failing because CloudFormation's tag syntax was wrong in the template. The thing is the syntaax I expected it to be was passing the YAML validators, and was described that way in the documentation. I submitted documentation feedback to update the example YAML snippet for an S3 bucket resource to reflect the proper tagging syntax more precisely. Unfortunately, if rollback is enabled the console wasn't depicting the specific reason the S3 bucket was not being created. When I disabled rollback the error message denoting the issue with the tags displayed. This was a super easy fix to implement, but, overall, the debugging process was subpar, and it's a bummer the bug was from a lack of clarity in the documentation. I'm really glad AWS has a feedback button for their docs to submit issues. I've only had to use it a few times, but it's times like these when I'm glad I'm able to play my part in others not bumping into the same issue I just did. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 60](#day-60)
#### June 30th, 2019
**Today's Progress**: 
- Wrote an initial cut of a CloudFormation template that uses an S3 template as a nested stack
- Configured a CI/CD workflow for the CloudFormation templates with CodeCommit, CodePipeline, and S3

**Thoughts:** Realized I forgot to post yesterday! Really getting into a development flow with writing CloudFormation templates and configured a CI/CD workflow for my CloudFormation templates to S3!

Keeping this brief becauuse I'm writing this on Day 61. The thinking that getting a directory structure sorted for nested stacks versus cross-stack references and getting reacquiated with CloudFormation's template anatomy paid significant dividends! Making a copy of my "template template", moving through each section, and having the resource reference documentation open while describing the S3 bucket configuration I wanted made creating a cut of the template really smooth. 

Previous #100daysofcode experiences getting familiar with the AWS Developer tooling made setting up the CI/CD pipeline a breeze we well. Fortunately there were no issues referencing the template I wanted from CloudFormation, and it using the nested stack I wanted per the references. I basically updated the script on my local, pushed it to the CodeCommit code repository, that kicked off a CodePipeline, which deployed the updates to the S3 bucket housing my CloudFormation templates. 

When I went to iterate over deploying the CloudFormation template I began running into error messages that weren't clear exactly what the problem was. Typically this means I'm looking in the wrong place for feedback on the execution. Determining that location and continuing to iterate through the issues is Day 61's tasking! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 59](#day-59)
#### June 29th, 2019
**Today's Progress**: 
- Reacquaited myself with CloudFormation's ["template anatomy"](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html) by creating a template for cfn templates with some quick reference comments and reminders about the different sections
- Figured out my development workflow for updating and storing CloudFormation templates
- Structured the repo I'd use to store CloudFormation templates by laying out and documenting how I'd treat different stacks for different courses, nested stacks for those courses, and cross-stacks to be used across all courses

**Thoughts:** Settling back into CloudFormation led to a worthwhile day of reading AWS docs and setting things up! Happy Saturday!

Starting the day I came up with a migration plan for the moving the groundedit.solutions domain to the Grounded IT Solutions LLC AWS account. It was weighing heaviest on my mind, but after thinking it through it turns out the groundedit.solutions website might experience a little bit of downtime maybe while the name servers of the new hosted zone switch over, and will take a minor, global performance hit when associating the new CloudFront distribution with the domain via the new hosted zone. I think that's it. Those are also the last steps; There is still moving the website itself, creating the deployment workflow, and maybe codifying it with CloudFormation (if I'm feeling peckish) prior to the DNS & CDN switches that could cause some weird behavior with the website.

After I had allayed those concerns I set my sights to creating the CloudFormation templates for AWS DevOps with a static site deployment. This had me revisiting best practices in organizing CloudFormation templates, using nested stacks versus cross-stacks, and the general "template anatomy" of a CloudFormation template. This deep dive in the docs was very necessary if I want to get fluent writing and debugging CloudFormation templates. 

By the end of the day I had a very commented up version of AWS's initial template to use as a starter for my other CloudFormation templates. This should allow me to move very quickly creating different nested stacks, then using them in a primary CloudFormation template that brings everything together. 

I'm being careful to not use "import" and "export" to describe using nested stacks. In the CloudFormation documentation import and export indicated one was using cross-stacks, which references a specific resource. An example is if you wanted to deploy everything into one VPC you would import a VPC's ID using a cross-stack reference. Then, that specific VPC will be used wherever it is imported. If you wanted a VPC with specific configurations, but not the same VPC every time, that's when one would want to reference a CloudFormation template that outputs a VPC as a nested stack. 

Looking forward to tomorrow when I should start iterating over CloudFormation templates that create the AWS resources necessary for an AWS DevOps complete deployment of a static site to S3!

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 58](#day-58)
#### June 28th, 2019
**Today's Progress**: 
- Began representing static website DevOps deployment to an S3 bucket in CloudFormation

**Thoughts:** Sorting out a CloudFormation CI/CD deployment of a static website! 

While this operation is fairly straightforward and already had [an example CloudFormation script in the documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/sample-templates-services-us-east-1.html#w2ab1c23c42c13c35) I realized I had a little more to think about. When I had worked with CloudFormation example templates in my last job as a proof of concept I'd realized the provided example don't always fit the context precisely, resulting in errors or...overcomplexity (not sure that's a word). An astute review of sample CloudFormation templates could resolve oversights down the road. 

When getting into the sample template I noticed the resources I already had set up wouldn't align with this template's assumptions. There were resources allocated for Route 53 when my account didn't have the hosted zone to add a record for the domain I was planning to use. This made me step back and realize several things were out of line. After a bit of thinking, instead of forcing a round peg into a square hole I opted to build out the CloudFormation template assuming it would be run in the main/parent account of my AWS Organizations situation. 

Surprise! The domain I had planned to use was still hosted from my personal account! Tomorrow's challenge will be figuring out how to transfer a domain between two accounts where I'm both the owner, but with different identifiers. An easier way to say that is I'd like to transfer a domain between my personal and business accounts. I knew this was a possibility acquiring the domain prior to having my business AWS account set up, but I made that decision, and now I'm going to sort myself out of the consequences! Welcome to small business owner life! 

P.S. Was fighting off a cold this week, so opted for naps or sleep instead of espresso shots yesterday. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 57](#day-57)
#### June 26th, 2019
**Today's Progress**: 
- Check that multiple deployments don't replace the files in the S3 bucket

**Thoughts:** Confirmed a suspicion that successive deployments weren't removing files that were no longer present in the deployed repository. Investigated AWS's recommendations and alternatives!

At some point yesterday I noticed the Date Modified time stamp of the files in the S3 bucket deployment target were mostly the same, but some were different. That had me concerned files that were no longer part of the latest commit in the branch being deployed were not being removed from the S3 bucket. Ideally this cruft would not exist. 

It makes sense that AWS would not by default delete files from an S3 bucket. While an argument could be made that the S3 bucket could be wiped prior to the deploying the latest static files, that could result in brief, but undeniable downtime for the website. Conversely, using a caching solution such as CloudFront could further alleviate the chances a user would notice any downtime within the second or two the files were being replaced. It's the prudent move for AWS to not make a design assumption that would temporarily take a user's service offline. Besides, any time a hosting service has the permission to delete files without, at least, the confirmation of the local party, it's a sketchy situation.

AWS's guidance in this situation is basically to create your own CodePipeline stage to set up the deployment target the way you would like. More mature deploymment workflows would adopt immutable deployments. Instead of modifying an existing deployment target, a new deployment target, like a server or an S3 bucket, would be created and deployed to. While that is the theoretical ideal, I'm not sure how to handle the complexity of replacing an S3 bucket when deploying a static site on AWS. It would end up being an update to Route 53, pointing an AWS ALIAS record from the domain name to the new S3 bucket url. My concern is I am not sure how this would effect any CloudFront configurations. It's possible it wouldn't, but that's why one of my next areas of focus is CloudFront! It's to be determined whether or not I visit CloudFront after working with CloudFormation to codify these static site deployment pipelines! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 56](#day-56)
#### June 25th, 2019
**Today's Progress**: 
- Debugged some issues with the GatsbyJS site that ended up being due to buildspec.yml misconfigurations

**Thoughts:** Resolved some buildspec.yml issues that was causing problems with the deployed GatsbyJS site! 

It turned out the directory being deployed to S3 was flattening out all the files underneath it. However, when network calls are made from the client-side back to S3 as with routing and images, the expected file structure isn't there. This took moving around some configs in the buildspec.yml file. Ultimately a simple resolution. 

I was surprised at one point when I attempted to kick off a build directly from CodeBuild. Apparently, the user I was signed in as doesn't have the permissions CodeBuild adopts, I guess, to perform the required tasks. If I kicked off the same build through CodePipeline, the artifacts were able to be put in the S3 bucket the previous run didn't have access to. It's intriguing in that what seemed to be similar actions taken through the console were actually run by two separate users. This is why it's essential to think about what is going on behind the console, instead of relying on "Click Ops". 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 55](#day-55)
#### June 24th, 2019
**Today's Progress**: 
- Debugged CodeBuild project and CodePipeline pipeline issues when deploying a GatsbyJS site to S3

**Thoughts:** Working CodeBuild/CodePipeline deployments to S3 of the default GatsbyJS static site! 

The issues with the deployment pipeline were all resolved with changes to the buildspec.yml. Pretty standard stuff: Updating some out-of-date paths, installing dependencies, and some shell command arguments being in the wrong order. 

An assumption I made that turned out to be wrong was CodeBuild was supposed to output a build file. Rather, it couldn't "output" a directory. The [CodeBuild Build Specification Reference](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html#build-spec-ref-syntax) notes that it is an option to include a directory and all the child contents, recursively. That's done by specifying `path/to/dir/**/*`. I hadn't referenced a directory with all it's child contents in this way before, so it was exciting to use a different shell command argument! 

Once the static site was deployed it appears routing is not working and the GatsbyJS homepage image is being rendered from an image that's about the size of a favicon. It's really blurry. Tomorrow will consist of getting to the bottom of those problems. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 54](#day-54)
#### June 22nd, 2019
**Today's Progress**: 
- Attended DCJS meetup
- Chatted with a few folks about GatsbyJS
- Learned about managing state with GatsbyJS
- Reviewed the AWS DevOps with a static site course curriculum with Jack from DCJS

**Thoughts:** Attended a DCJS meetup and learned more things about GatsbyJS!

I think it's so fun to attend coding meetups and discuss with folks what they are working on! I come with a project in case things are slow for whatever reason. Today I was able to have several chats about various topics. I didn't get back to working on CodeBuild, but I can pick that up again tomorrow when there isn't a meetup on my calendar. I did notice that CodeBuild has documentation on lots, if not all of the errors it throws. That will be where I start tomorrow! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 53](#day-53)
#### June 21st, 2019
**Today's Progress**: 
- Set up a GatsbyJS repo practice building with CodeBuild
- Authored an initial buildspec.yml file for CodeBuild
- Learned how to get feedback on build issues within CodeBuild
- Began iterating over buildspec.yml file

**Thoughts:** Today was about familiarizing myself with CodeBuild! Began building a GatsbyJS project with CodeBuild!

The feature to deploy static sites directly to S3 with CodePipeline presupposes a codebase with no build steps. Frankly, it would be pretty uncommon these days for a front-end developer to work on a website without incorporating any build tooling. They would be writing plain HTML, CSS, and JavaScript when abstractions and/or transpilers exist for all three. More importantly, techniques such as minifying plain HTML, CSS, and JavaScript to assist with performance delivering the static site over a network are quite common. While murmurs of a "back-to-basics" mindset for front-end development have been appearing on my newsfeeds, but legacy, "single page app" client-side codebases most developers will find themselves adopting will require a build step(s) before deployment. 

That makes CodeBuild an essential aspect for DevOps of a static site on AWS. The service appears to act as as the master CI server that spins up build servers to perform the build steps. It asks whether you have a specific container you'd like to use to build your codebase, or if you can rely on their standard build servers. GatsbyJS requires some pretty common prerequisites and abstracts their build process into one command. It's a really solid candidate for my use case -- Incorporating a build step into a static site deployment. 

So far so good! A buildspec.yml is a file CodeBuild can use for instructions on how to build a codebase presuming the buildspec.yml file is included at the top-level directory of the codebase. The documentation associated with creating a buildspec.yml file is really straightforward. At the bottom of the documentation they have a changelog of the buildspec.yml file. Apparently there has only been one minor version bump since the init! That feels like an impressive initial design to only need one minor version bump since inception. At this point I'm using feedback from the CodeBuild web console to iterate over the buildspec.yml file. Once all that is sorted I'm expecting to be able to have automated deployments, with build steps, to an S3 bucket hosting a client-side codebase! 

FWIW, yesterday I took a day off from #100daysofcode because I learned of a surprising cash flow situation with the business surrounding these online trainings I'm hoping to produce. I had presumed that the training platform I'd use deposited my cut of the revenue from sales into my business's Paypal account shortly after the sale occurred (like, as soon as their system processed the sale). From what I had read up to this point the language was, in summary, "sale happens, they deposit money into your associated account". It turns out that is not the case! Initially, the training platform does nothing with the sale for 30 days because the customer can request a refund in that time. Then the training platform asks 30 days for their systems to process the sale. 

It's worth noting they are processing sales from around the globe with lots of variables; They have to reconcile differences in currency, their taxes, fees from transfers to instructor accounts, couponing, analytics in their internal systems, auditing the sale for fraud from instructors, etc. . In other words, they have lots of things to cover. After those 30 days, payments to instructor's account occur from the 6th to the 8th of every month. My initial reading of the guidance that someone enrolls in my course and within minutes or hours I see a deposit into my instructor account was wrong. 

I took the day to figure out what to do with that, assess the runway (i.e. savings) I have allocated to build the trainings to support myself, track my expectations appropriately, and get comfortable with reality. It was tough to focus on anything technical when in the realization smacks you in the face that you won't get paid for your work shortly after the product is purchased, but at least two months after the product is purchased! Fortunately, speaking a small business owner, I can handle this cash flow happenstance. Still following through on getting these trainings published!  

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 52](#day-52)
#### June 19th, 2019
**Today's Progress**: 
- Brainstormed how to present why different environment branches exists
- Researched how to limit access to a static website or folders hosted on an S3 bucket

**Thoughts:** Dug deep into why different environments have existed in my past professional life and researched different ways to restrict access to S3 buckets! 

Approaching my learning as if I would be teaching the system to someone else has me really digging into the details! I'm sure there would be opinions about what environments I use in each course and how I've followed  through on the security restrictions between environments. Instead of moving forward with building the pipelines, this has me constructing justifications as it why something could be done a certain way. 

An important aspect to emphasize to folks taking Grounded IT Trainings is that many technical decisions are guided by context. Yes, there is an "ideal" way to do things, but that might not be an option with a certain workplace. This creates a grey area; When the "right" choice isn't an option the decision becomes taking the "least bad" option. Experienced teams won't let the least bad option become the status quo, but realizing it's a choice that's made for the aggregate benefit is pragmatic thinking. With the content I'm putting together I want to present several options, emphasizing the positives and negatives of each approach so viewers will be able to work back from the best to what is possible.

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to configure custom subdomains of groundedit.solutions to use for S3 buckets and other resources hosted in child accounts
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 51](#day-51)
#### June 18th, 2019
**Today's Progress**: 
- Figured out CI/CD workflow and its integration with branching strategies

**Thoughts:** Read lots about branching strategies, chose then tailored one, and laid out how to integrate it with AWS's CI/CD Developer Tools!

Most days I sit down feeling like I have a clear idea of what I am going to work on. Occasionally, I'll learn something early in the day that thwarts my initial plan. In this case, I realized that branching strategies end up getting tailored to whatever local context they are being used in. I was thrown by this for a bit because I want to build an online course that adheres to the best practices. How do I adhere to best practices when there really isn't a best practice, just a few frameworks for approaching the same problem? 

I read about several branching strategies, taking bits from each, mixing it with my on-the-job experience, eventually settling on a tailored version that resembled my ideal branch workflow. This had to account for the different possible CI/CD pipelines I wanted to build. Most importantly, though, it had to be coherent enough for me concisely explain. 

The primary tweak I added to the Gitflow branching strategy was changing the "master" and "develop" naming convention to a more semantic, flexible, and scalable naming convention. Instead of "master" each environment's branch will be env-*, with * representing whatever that environment is named. Naturally an order to which environments are updated will arise (typically testing, then staging, then production). Release branches would replace the "develop" branch. Feature branches would be named with the release they are associated with. So each release branch would end up being an integration branch for the features in that release. 

There are several gains to this approach. First off, CI/CD pipelines and environments can be built around the env-* branches. Release and feature branches would clearly be separate for for code integration or development. With release planning, the onus would clearly be taken off the developers. Team leads or Managers can plan feature releases farther out, and developers can work and merge those apart from the current release branch. The feature branch could be closed after the release has been deployed. New branches after that would be bug fixes. The use of release and bug fix in the naming convention also aligns with semantic versioning. It will be clear that a feature aligns with the 0.x.0 number, while bug fixes align with the 0.0.x number. 

As with any system, ideally hot fixes don't happen. They probably will, but in this workflow it is especially beneficial to avoid hot fix branches. A CodeBuild pipeline can be set up to house all the build steps to create a static bundle for the static site being deployed. Hotfixes to prod that cause build steps to fail might then cause developers to update the CodeBuild steps. However, if the same CodeBuild configuration is being used across all the environment branches, this could break the state of earlier environments. While it can be a marginal tradeoff to make, on the whole it further discourages the use of hot fix branches. 

I'm enthused about the git workflow, and emailed a friend asking how customizable he felt branching strategies are impliled to be these days. I diagrammed out this branching strategy, the CI/CD workflow, and the AWS Developer Tools I'd use to implement it. Looking forward to tomorrow for sure!

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 50](#day-50)
#### June 17th, 2019
**Today's Progress**: 
- Dug into configuring a CodePipeline...?pipeline? using CloudFormation
- Learned a bit more about configuring S3 bucket policies
- Deployed a simple static website with CodeCommit and CodePipeline to S3

**Thoughts:** Learned about CodeBuild and set up a simple CI/CD pipeline for a deploying a static website with CodeCommit and CodePipeline to S3! 

I was wondering how long it would take to get this pipeline configured. It feels like it is a really straightforward service for AWS to provide, but I had never used CodePipeline to deploy anything before. At my last job we went with Jenkins because it was an established tool around IT. We figured it would be easier for our organization to adopt its use if our group could showcase how to enabled CI/CD best practices. We used Jenkins Pipelines, which felt similar to CodeBuild's YAML file configuration to handle the instructions for processing builds. Setting up this continuous integration workflow technically could be three servers or fewer: A version control server where the repository is hosted, a server to process the build (in this case just copying some files), then a static file server. It could be accomplished on one server, but I'm pretty sure the Ops Gods of the universe will curse your existence for not segmenting the roles onto different boxes. 

Today I learned that comparing Jenkins to one of AWS's Developer Tools is a misnomer. Jenkins core feature set coupled with the plugin ecosystem really covers a combination of AWS's Developer Tools used together, not just one. I also learned that deploying directly to S3 is something that [recently became an option](https://aws.amazon.com/about-aws/whats-new/2019/01/aws-codepipeline-now-supports-deploying-to-amazon-s3/)! Mentally I was approaching familiarizing myself with AWS's DevOps tooling with the most straightforward, simpliest use case. I did not expect it to be a feature that feels bolted on. 

I can understand how the definition of CodeBuild and CodePipeline can conflict regarding where to put this feature. CodePipeline is by definition a continuous delivery tool, which basically tracks releases in an automated fashion (to water down AWS's definition). CodeBuild, on the other hand, is a continuous integration tool; It handles the build steps to actually deploy your application. Deploying a static site directly to S3 falls in between these two toolsets. I can see the conversation happening at AWS's HQ; Should deploying directly to S3 from version control be a CodeBuild feature or a CodePipeline feature? Especially if the teams don't overlap the product managers could have had a meeting or two figuring this out. Or it was a water cooler conversation concluding in high fives, who's to say, but if I were a betting man I'd wager this conversation happened. 

Circling back, the feature to deploy a static website from version control directly to S3 feels bolted on because the configuration options to check presume there are build steps in between. This completely makes sense. In spite of the "Keep It Simple, Silly" wisdom that floats around IT, even static sites these days can have tons of build steps. I guess I was expecting the deployment target line of questioning prior to being asked about before CodeBuild was asked about. I think I'm writing in a loop though; If I had known the purpose of CodeBuild and CodePipeline prior to attempting to create this CI/CD pipeline I would have known CodeBuild is for build steps, and I don't have any build steps if I'm deploying the static files directly from a version control repository. The option to skip the CodeBuild step would've been the clear choice.  

Even with static websites I'm realizing how deep the rabbit hole can go as far as configurations are concerned. Hosting static files on S3 is easy enough; Want to have your static file globally distributed using CloudFront to reduce latency? Want to capture and update your CI/CD pipeline as infrastructure-as-code? Want to follow a best practices gitflow while having your CI/CD pipeline deploy feature branches to an isolated network for review and approval away from the world? Want to have all this at the lowest price possible while sacrificing as little as possible? There is lots to do! On to tomorrow! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 49](#day-49)
#### June 14th, 2019
**Today's Progress**: 
- Validated accessing a child account using a cross-account role
- Got my hands dirty with CodeCommit
- Configured access to a git repository hosted on CodeCommit using a cross-account role

**Thoughts:** Using a cross-account role to access a CodeCommit repository via local git had my eyes crossed at times thinking it through, but it worked like the instructions said in the end! https://docs.aws.amazon.com/codecommit/latest/userguide/cross-account.html . Didn't count yesterday in spite of learning a ton after reading answers to the latest questions on reddit.com/r/aws!

At this time it appears the AWS account structure for my company is a master company account with several project accounts underneath that, one project account for each online course I'll end up creating. The thinking is when that online course is published that account can host whatever example is necessary, or, ideally, have all of its resources from the course shut off, zero cost, with the architecture stored in a CloudFormation templates. There might be some CodePipeline deployment steps there was well, but I'm not familiar enough with CodePipeline to say. The costs from the sub-accounts will be paid using consolidated billing, but I'll still be able to break down the costs on a per account basis. This should scale for the time being; I think the limit of AWS accounts under AWS Organizations with 30 accounts? I might be mixing up a different limitation though. 

I've settled on the idea that systems will beget courses, so instead of trying to craft the perfect course I will build a system, create a course about it, and increase complexity in the systems over time. Worst case, I'll have built several systems with courses that don't sell (but, on the bright side don't have any customer support to tend to) and have that system experience under my belt. Earlier in the week I read about interviewing at Google. The author was, apparently, a technical person that conducted those interviews at Google. They said that they expect any system prototype to take one to two weeks. That's quite the generalizaiton, but working to meet that standard I should be able to build out most systems and their course content throughout a month. 

In working through this particular system, one of the first steps is storing the code in version control. I had set up a github account earlier in the week, but it feels appropriate to attempt an all AWS pipeline first. I can reconfigure things to use other version control to show how that is done in the courses. It will make things more comprehensive. Also, one would need access to my AWS account to authenticate with the CodeCommit repositories; So they are private by default. 

Getting started with CodeCommit was straightforward enough. What complicated things a little was using my IAM user from my master account to access a repository hosted in a project account from my local terminal git. Fortunately, AWS had thought about this and [provided some detailed instructions](https://docs.aws.amazon.com/codecommit/latest/userguide/cross-account.html). I like how they presume you haven't configured the cross-account role yet. I was able to skip ahead to the last step after validating I had followed the cross-account steps as expected. 

The main downside to using a cross-account role to access a CodeCommit repository is AWS does not allow connecting over SSH. That leaves HTTPS as the authentication mechanism. We'll see if this has any effect on my dev workflow, because I remember before configuring SSH with Github it got pretty annoying having to type in my username and password everytime I wanted to push or pull updates, if I remember correctly. 

My eyes began to cross setting up the different accounts I wanted to use to access different AWS accounts or Github respositories using git. Now I have a company AWS account I use for updating my company AWS things, a personal AWS account for the same, and a Github account for Github repositories. I've got at least one more to incorporate with Gitlab, but now that I've gotten to this point I'm more confident adding one more. With that said, it's done! I was able to authenticate and pull from the CodeCommit repository. On Monday at the latest I'll pick up building out the system for DevOps of a static site workflow on AWS! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 48](#day-48)
#### June 12th, 2019
**Today's Progress**:
- Created an AWS account under my AWS Organization for specific project work
- Created a github organization to host company repositories
- Created a simple static site on s3
- Researched how to set up a devops pipeline on AWS for updating a static site

**Thoughts:** Getting a feel for how to use AWS's DevOps tooling to update a static site!

Earlier in my 100 days of code/cloud I set up a static website on S3 that is cached using CloudFront and served over HTTPS. Now I'd like to configure a deployment pipeline with version control integration. [This great blog post describing how to implement GitFlow with AWS's Code* DevOps tooling](https://aws.amazon.com/blogs/devops/implementing-gitflow-using-aws-codepipeline-aws-codecommit-aws-codebuild-and-aws-codedeploy/) (CodeCommit, CodePipeline, CodeDeploy, CodeBuild, ...etc.? TBD?) has been a solid jumping off point so far. 

It's getting difficult to think of a scenario when I wouldn't implement one of these setups as infrastructure-as-code, so there will be CloudFormation templates to spin all this up. If I see a tutorial with screenshots of the console and no link to a CloudFormation templates it frightens me. "ClickOps", as I think someone called it on a podcast, makes me think of clients saying "We have someone that knows the code/software/process/configuration/architecture/thing. They handle that.". It feels rare that someone ultimately responsible for an AWS account would take the time to audit the CloudTrail logs or review the current configurations using AWS Config. It's naive to assume they would treat CloudFormation templates the same way, have a record of them running, and be able to review the latest run with ease, but it's something to strive for! kAt least version controlling the infrastructure would give a historical record of changes to the templates, with who made those changes. Yay accountability! 

Proper organizational oversight of the activities going on in different cloud accounts feels like a problem that requires significant overhead to resolve at the moment, when it should be something built in. Like, click-button enable the feature, then anyone with a particular role is able to review a dashboard of the latest configuration changes to an AWS account and is alerted when there is a certain amount of activity occurring on the clould account. Maybe I'll get into that sometime, but for now it's getting this static site devops GitFlow, infrastructure-as-code project, live, working, demoable, and ultimately, teachable. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 47](#day-47)
#### June 11th, 2019
**Today's Progress**:
- Learned about when to use Object Oriented Programming languages versus when to use Functional Programming languages
- Read about the ["Expression Problem"](https://eli.thegreenplace.net/2016/the-expression-problem-and-its-solutions/) in programming languages
- Investigated how to ensure servers are stateless with Node.js and Ruby on Rails applications
- Investigated creating a graphql server using Node.js
- Did 10 more AWS DevOps Engineer study questions

**Thoughts:** Answered some questions that had been nagging me after the reading yesterday, such as when to use OOP vs FP and how to ensure stateless app servers!

Today turned into several connected google sessions after thinking through what I had learned yesterday. It was nagging me that someone had mentioned in one of the articles that functional programming languages had gained popularity because it's better for maintaining a stateless codebase. A few years ago I gained some experience with Ruby on Rails, and knew scaling a Rails app could be accomplished through horizontal scaling. But Ruby being and OOP language, how did Rails accomplish stateless servers and what made functional programming languages the better option?

It turns out the Ruby on Rails answer is straightforward. Each request is handled by a new instance of the Rails Controller class. So the state is only maintained through the lifespan of responding to the http request. That's pretty neat! [Avram proves this in this blog post](https://medium.com/@avram/the-state-of-your-rails-app-is-stateless-f7dea177a5f4).

The "answer" to the second question is a little more nebulous to me. It's one of those answers that will get clearer over time with experience, but, right now, I'm having trouble thinking of different use cases. [This stackoverflow response](https://stackoverflow.com/questions/2078978/functional-programming-vs-object-oriented-programming) is the broadest, most applicable response. It boils down to OOP languages and concepts are best used when there are a set number of operations on things, with more things being added over time. FP languages and concepts are most effective when you have a fixed set of things, but your operations will change over time. 

This has me thinking the choice between writing applications in an OOP language versus a FP language is less about writing stateless code and more about the future requirements you expect to be requested after the MVP is accomplished. It's nice to know that either will do!

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 46](#day-46)
#### June 10th, 2019
**Today's Progress**:
- Read [Google Cloud's post-mortem of their outage on June 2nd](https://status.cloud.google.com/incident/cloud-networking/19009)
- Read Chapter's 3, 5, and 6 of ["The Complete Guide to Google Interview Preparation"](http://blog.gainlo.co/)
- Reviewed AWS Control Tower and AWS Landing Zone
- Watched several "This is my architecture" AWS videos on Youtube

**Thoughts:** Lots of reading today! Google Cloud's post-mortem, the systems design & coding portions of a guide to interviewing at Google, and overviews of AWS Control Tower & Landing Zone services! 

When I opened my laptop from Friday I had several tabs open with articles I didn't end up getting to on Friday. They seemed relevant to what I was interested in today, so I dove into them.

Google Cloud's post-mortem was fascinating! Occasionally these post-mortems can come across as techy, PR jargon that's meant to obscure what was a pretty straightforward issue (like a cert expiring, or something). I would say that Google Cloud's port-mortem wasn't this. It really appears to be an open breakdown of the issues that occurred from all sides. My rudimentary understanding is it boiled down to two bad configs that caused services to stop (this is by design), network control plane clusters being marked as ineligible, a bug that expanded the breadth of an impact to multiple clusters and "physical locations" (so datacenters?), a failover to prevent UX degradation that didn't last long enough for engineers to be alerted and resolve whatever the situation was, and subsequent network congestion on the same network their tooling to monitor and debug the original issue was using. So their tools to fix the issue weren't loading well/quickly. Really fascinating! It's a bummer it happened, but as a solutions architect looking to level up their skills, open post-mortems like these are a glimpse into huge production architectures, how they work, and how they can break.

Chapters 3, 5, and 6 inspired me to get a concrete plan for progressing on my 100 days from here. I found the coding challenge sites I had used previously and determined my favorite resources for learning about systems. Between a few code challenges a day and some systems architecture study I should be kept organized and learning for the next few days at least :-) . 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 45](#day-45)
#### June 7th, 2019
**Today's Progress**:
- Reviewed the systems design resources mentioned in [this blog post](https://medium.com/@XiaohanZeng/i-interviewed-at-five-top-companies-in-silicon-valley-in-five-days-and-luckily-got-five-job-offers-25178cf74e0f)
- Followed up with several contacts about my recent IT work, including creating an architecture diagram 

**Thoughts:** Pretty light day, but found several more resources online to grow my skills referencing this blog post! https://medium.com/@XiaohanZeng/i-interviewed-at-five-top-companies-in-silicon-valley-in-five-days-and-luckily-got-five-job-offers-25178cf74e0f

Getting an offer at all five Silicon Valley companies after a week's worth on in-person interviews is an impressive feat. Rightly so, Xiaohan Zeng's blog post went viral as far as I can tell. 51k+ claps on medium and translated into three languages is quite the community validation. There is a section on how he prepared for the systems design portion of the interviews. I had to take the time to review it. This blog post has been linked on the home screen of my phone for probably a year now; I look at it whenever I'm daydreaming about how to level up my technical skills. 

Surprisingly, some of the blogs were older than I expected. Xiaohan's blog post was published in 2017, but some of these blogs hadn't had a substantive post since 2016 at the latest. I didn't rule them out completely because every study has its fundamentals. Regardless, it's prudent to know how today's thinking came to be. Tracing the thought back through old blogs posts is a taxing exercise, but really solidifies understanding. 

I'm realizing about once a week I have a day where I don't actually end up creating something tangible. Like, if someone random were to come up to me in the coffee shop and ask me what I'd done today, I want to be able to show them something that I think is cool. I'm proud of what I've accomplished so far doing 100 days of code, but I am alright with these days coming up once a week. It seems to arise at a point where I need to reorient my efforts, even if what I've been doing has been beneficial. It's as if something, be it my goals with my daily tasks, or something like that get out of alignment, I naturally settle back and realign with what's important to where I'm ultimately aiming. It's also Friday, and who wants to figure that out on a Friday afternoon. Save that for Monday morning with a fresh espresso! :-) 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 44](#day-44)
#### June 6th, 2019
**Today's Progress**:
- Looked into and learned more about consolidated billing
- Learned about how to restrict access to running resources in different regions
- Enabled billing alerts by setting up a budget
- Followed [this blog post](https://aws.amazon.com/blogs/big-data/streamline-aws-cloudtrail-log-visualization-using-aws-glue-and-amazon-quicksight/) to process, query, and analyze CloudTrail logs
- Configured CloudTrail to track all regions and enable log file validation

**Thoughts:** Wrapped up configuring my new AWS account and stepped through a neat blog post about processing CloudTrail logs; The solution used CloudFormation, S3, Lambda, Glue, & Athena!

Walking through setting up an AWS account while following as many best practices as I can has been an eye opening exercise! I'm an AWS Certified Solutions Architect - Professional and amount of different screens I've had to visit to configure all the things properly has been surprising. If I was a small business owner first coming to AWS it would be easy to get the payments set up and start spinning up EC2 instances myself. But the amount of best practices that goes into managing an AWS account for an organization quickly starts to add up! First off, there's knowing what services do what thing. Once you've got that sorted it's using them properly for provisioning access, auditing, controlling costs, and then scaling all those operations. Then it's navigating the console to configure all those things!

It's worth noting the documentation also suffers from this fragmentation. I would stumble across a web page of AWS documentation that began to bring together all the best practices for setting up an AWS account. The most obvious example is [the IAM best practices page](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?icmpid=docs_iam_console). However, they all suffered from the same issue that the best practices were limited to that one service. It makes sense that this is the case given how AWS's documentation is organized by service anyways. With that said, a link list to as many of these pages as would be relevant for someone setting up an AWS Account for the first time would help new AWS users grasp what it takes to properly manage a cloud services account. For organizations, this would help mid-level IT managers realize that following the enterprise's lead would allow for synergies across accounts, such as consolidated billing, budgets, and the capability for organization-wide CloudTrail auditing, just to mention a few gains. It would be in AWS's best interest to make it easy to stand up an account and start spinning up resources, but it would be in the user's best interest to have receive a bit more guidance on how to manage and oversee the account properly.

I suppose stepping through setting up an account and accommodating as many of the best practices has beeng great experience this week. It's rare that at a job one would get to stand up an AWS account from scratch. Typically, the team would've already done that. But I am getting to the point where it's better for me to move onto different topics. My company AWS account is set up enough to start architecting under the company name securely while controlling costs. At this moment I'm thinking I'd get my hands dirty with SQS, autoscaling EC2s to ingest the SQS queues, the ops around that type of thing, then maybe pivot to AWS Kinesis from there to handle use cases with the asynchronous processing of real-time data. Onward! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 43](#day-43)
#### June 5th, 2019
**Today's Progress**:
- Figured out how to add a custom attribute to G Suite users
- Tested SSO with the updated custom attribute. No luck. 
- Enabled MFA for the root user and checked that the root user did not have any active access keys
- Read about AWS Organizations and configured it appropriately for Grounded IT Solutions's AWS Sccount at this time
- Created an Admin group with a corresponding administrator policy for the account
- Created a new user to use instead of the root account and ensured I could log in as that user
- Aliased the account to make the url for logging in easier to remember

**Thoughts:** Learned the practical uses for AWS Organizations and logged in as an admin user besides the root user, per best practices! Not a crazy day, but an essential one. 

Initially started the day trying my hand at the G Suite SSO again. After stepping away and thinking things through a bit more, I figured there must be a way to add a custom attribute because there are so few. Turns out there is a way; It's an icon on the G Suite page that lists all the users. I tried adding a custom attribute that would map to the AWS Default role for G Suite users. SSO from G Suite to AWS still didn't work, but I feel more confident I'm understanding the pieces and have nearly all of them in place. AWS doesn't really provide an actual error, just that it received a bad SAML request. One key thing in debugging network stuff is having some log to look at to get detailed errors about what's going on. I'm not really sure how to access that. It could be in the network tab of developer tools. If that were the case though I'd still want it to be more accessible to the common user. Yes, it would probably be an IT person setting up SSO between G Suite and AWS, but they shouldn't need to open up dev tools in order to get a useful message. 

Continuing with the best practices to do list I came up with a few days ago had me digging through AWS Organizations documentation. I like how it provides an overarching view and management of several AWS accounts. That visibility is really neat, and allows an organization to have several accounts for one business. Practically speaking, thinking of [Service Control Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html) acting as the "guardrails" for an organization concerning which AWS services different accounts can use. This can be a really useful function if an organization isn't sure how it wants to handle machine learning services, or doesn't want to fragment its core IT services by allowing its child AWS Accounts to sign up for WorkMail, or something like that. While I haven't seen the consolidated billing feature of AWS Organizations yet (maybe because I don't have a bill), I can see how AWS's consolidated billing across all these accounts with Service Control Policies would allow a CTO shop to keep certain AWS services from being used until they are sure they know how the internal policies around using that service or cost projections with that service would work. I'm not sure I 100% agree with this approach, it's a little too hands on, but it would allow a CTO shop to double-check any cost projections of child accounts. Like, a child account wants to do some machine learning. Neat, what EC2 are you going to run that on? Are you sure you're going to be able to train your models fast enough on that much compute. I don't know machine learning stuff well, but I could see how a child account blows past its projections if it doesn't estimate the amount of compute it'll need to train it's models. Now devs are going to need a hardware refresh sooner after they leave their underpowered machine overnight at the office churning on training the model. But you kind of do want the flexiblility of child accounts to use a wide array of AWS's innovative offerings to resolve their local concern. I guess it's a balancing act any way you slice it if you get a little overexcited with Service Control Policies. But I like that there is that capability! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 42](#day-42)
#### June 4th, 2019
**Today's Progress**:
- Began setting up my new AWS account

**Thoughts:** I'm enjoying configuring a new AWS account! Having some trouble getting SSO from G Suite working though. 

Once I was able to set up my business email I was able to follow through on the to do list from yesterday! There are a few things that at first glance aren't so clear. For example, I understand moving towards simplifying UIs, but I think it should come with some sort of toggle tutorial for how to configure some of the basic aspects of that service. For example, I set up AWS Organizations, but I didn't see where in the user interface to configure consolidated billing. I'm presuming that I need to have a bill from one of the accounts associated with that Organization first, but not sure :shrug: . Of course I'll end up browsing the documentation to see what I missed there.

Then I moved onto configuring SSO for G Suite into my AWS account. While the instructions seemed straightforward, I got to a place where it was difficult in Google's G Suite interface to deliniate what role should be associated with what individual. From what I can gather it seems a role needs to be associated with an attribute of a user, such as what Department they are in or what their first name is. Testing that conjecture failed though. I think I'll table this feature and continue moving through the rest of the to do list tomorrow. It makes it so I need to log into one place instead of two each day, so it's nbd. I bet an hour or two of chatting with G Suite support should clear the issue up. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 41](#day-41)
#### June 3rd, 2019
**Today's Progress**:
- Researched best practices for setting up a new AWS account

**Thoughts:** A bunch more reading about best practices when setting up an AWS account; Got a To Do list together to follow tomorrow! 

AWS account to-dos:

Configure AWS Organizations

Configure AWS SSO with G Suite to give read access to all things to anyone in Grounded IT Solutions LLC (https://support.google.com/a/answer/6194963?hl=en)

Use a group alias email with the account (i.e. cloud@groundedit.solutions) 

https://www.1strategy.com/blog/2018/04/24/creating-an-aws-account-a-checklist/

MFA for at least root user

No access keys on the root account 

Developer level support

IAM policy/role/user for billing access

Enable billing alerts (can these be dynamic? Like, if a bill is within 10% of last month's bill send an alert?)

Create AWS admins group

Create account alias (easy peasy)

Ensure CloudTrail is set to track all regions and enable log file validation. maybe do this https://aws.amazon.com/blogs/big-data/streamline-aws-cloudtrail-log-visualization-using-aws-glue-and-amazon-quicksight/

Use us-east-1

Turn on aws config. No rule checks, just tracking. Double-check after a month if it's costly given my activity. It would be surprising if it's more than $30 and I have no rules.

Create things through the console and using CloudFormation. No restrictions at this point. 

Some other things: 

See about using AWS organizations and follow project-based account structure

https://d1.awsstatic.com/whitepapers/cost-optimization-laying-the-foundation.pdf 

Tagging strategies - https://aws.amazon.com/answers/account-management/aws-tagging-strategies/

Hmmm, not sure which one to go with. Seems like Project-based is best long-term https://aws.amazon.com/answers/account-management/aws-multi-account-billing-strategy/ 

See next steps for MOAR security stuff - https://aws.amazon.com/blogs/security/getting-started-follow-security-best-practices-as-you-configure-your-aws-resources/ 

Use Trusted Advisor to clean things up as necessary - https://aws.amazon.com/premiumsupport/technology/trusted-advisor/ 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 40](#day-40)
#### June 2nd, 2019
**Today's Progress**:
- Researched best practices for setting up a new AWS account

**Thoughts:** Researched some best practices around setting up and configuring an an AWS account! Slowly but surely things are coming together for an IT services/training lifestyle business I'm bootstrapping outside of my 100 days of code work. One of the tasks I've been looking forward to is setting up an AWS account from scratch. Besides adopting as many of the best practices I can find, I'll be able to experiment with AWS Organizations, Cross Account Roles, and other interesting capabilities. 

Properly configuring an AWS account is one of those things that comes up frequently in an established organization, but is usually difficult to change. It requires someone high up enough to give approval to, say, enable MFA. Not a huge deal and definitely essential, but it requires middle managers to understand why the change is being made, make the change themselves, then follow up with their direct reports to ensure the rollout is succeessful. In that specific instance there are work stoppages if someone is having trouble configuring their MFA. Someone high enough up has to give the blessing that changing this configuration is worth the possible hit to productivity. Understanding the recommended ways to do this today, configuring the account as such, and learning about how difficult certain configurations would be to change later should make scaling the engineering portion of the business easier down the road. I mean, that's presuming there would be an engineering portion of the business to scale :-) . TBD! 

P.S. I don't like to have "research" days for my 100 days of code. I'd rather produce some sort of result each day. Research, IMO, should be time boxed and should come to something, whether a proof of concept or some deliverable. Fortunately, there is time pressure to get this AWS account spun up ASAP, so results will be coming soon. Also, for about two weeks now I've been following a path to create a React voting application. I'm at a place with that work where I can put a pin in it and pivot to something that is a learning excersise that yields impactful results for my other endeavors versus exclusively a learning exercise. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** (but really just a running list of other things I want to keep on the radar) 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 39](#day-39)
#### May 31th, 2019
**Today's Progress**:
- "Persisted" authentication state between page refreshes
- Completed a full sign up and sign in authentication flow

**Thoughts:** React app now maintains authentication between page reloads! Last week when I was following a tutorial the author used the term "persist" to describe handling authentication between page reloads. I'm not sure this is exactly accurate, because really what happens is as soon as the page loads, a network call is made to Cognito to determine whether a user has been authenticated with this particular client. Amplify does have the flag to check the cache first, but, if I remember correctly, it defaults to not check the cache. My point is the authentication doesn't so much "persist" on the client. It's really validated with the backend that this client has already been authenticated. The way I understand it, there is no data persisting on the client that is being checked.

I ran into an issue where I was causing one of my top-level components to rerender every time it attempted to render. Obviously, this was causing a hilarious infinite loop issue :-) . Fortunately, the folks at Facebook have built React to recognize this circumstance as it's happening. React short circuits the infinite loop before it can continue and throws an error. The fix was refactoring the logic to prevent the state changes from kicking off a rerender. I'm honestly not sure rerender is a word, but going with it anyways. Happy Friday! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 38](#day-38)
#### May 30th, 2019
**Today's Progress**:
- Continued incorporating AWS Amplify UI components

**Thoughts:** Successfully signed up with email verification and added global app error handling! I am really loving writing a React application with Hooks and managing global state using a custom Hook. So far, I've had no reason to write a class component; All my components are functional components. It's also much less boilerplate code than writing components with classes. It makes me feel like I can move really quickly creating components once the application is laid out. A former tech lead once mentioned how productive he felt once he was able to easily write React components for an application, then reuse those components as needed. I'm getting that same sort of feeling; It's empowering! We'll see what complexities either me or the community run into when React applications with Hooks are more widely used in production. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 37](#day-37)
#### May 29th, 2019
**Today's Progress**:
- Continued incorporating AWS Amplify UI components using React Router to configure the proper redirects

**Thoughts:** You can sign up and (almost) sign in using React with AWS Cognito! Incorporating each endpoint seems like it should be pretty trivial from here on out. One obstacle I can see coming up is making sure your user experience aligns with your Cognito User Pool configuration. For example, if the User Pool is configured for users to validate their email using a verification code, then you obviously need to have a component where a user can submit their verification code. 

Juggling the different authentication states was always something I knew I'd have to do. I'm nervous it's going to take a significant amount of time. Hopefully rendering all the components on one page, then showing or hiding the components depending the global state will help with getting the authentication flow sorted. I can refactor those interactions to use React Router to link to container components depending on the same states. That should facilitate that aspect, however that might be overfill as this is pretty much a throwaway application for practice. Getting to building out the AWS architecture is the priority activity of building out this system. 

Yesterday evening I attended [a local talk about using GraphQL and Apollo in a React app](https://www.meetup.com/React-DC/events/261428186). It was great! While listening to the talk I figured AWS must have a hosted solution for GraphQL, but I couldn't put my finger what it was called. Turns out it's [AWS AppSync](https://aws.amazon.com/appsync/). AppSync uses GraphQL and Apollo under the hood. Adding this to the list of AWS solutions I want to prove out using for myself! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- Start incorporating AWS Amplify UI components using React Router to configure the proper redirects
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 36](#day-36)
#### May 28th, 2019
**Today's Progress**:
- Attempted to write my own tooling for outputting the current application state and what action caused the current application state to change
- Start incorporating AWS Amplify UI components using React Router to configure the proper redirects

**Thoughts:** Wrote a little bit of middleware and began getting auth UI components put together! With the use-global-hook npm module I wanted to have the current state of the application outputted to the console. Ideally, anytime an action was called, the before and after state would get printed. I was able to get the current state to print everytime the useGlobal hook was called, but I had more trouble getting the action to print. I wanted to iterate over the actions object and (...maybe this is the right word...) decorate each action with a function that would print the action and the before/after application state objects. After about an hour of trying a few things, I had to move on to actually progressing getting the authentication flow to work instead of investing too much time into tooling. Every so often I realize I "don't know JavaScript" and I probably could do with a review of Kyle Simpson's books or some coding challenges to continue leveling up my JavaScript skills.

Did lots of laying the groundwork of different components that would act as the authentication flow throughout the application (sign in, sign out, sign up, etc.). Tomorrow I should get to actually hitting the endpoints to interact with the Cognito User Pools via the Amplify API. Once that's done I'll get to submitting my "vote" to the backend; That's when we're cooking with fire and can get to the SQS, DynamoDB, etc. aws architecture work! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- Start incorporating AWS Amplify UI components using React Router to configure the proper redirects
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 35](#day-35)
#### May 27th, 2019
**Today's Progress**:
- Configured eslint to check for best practices when using Hooks
- Watched the [introduction to Hooks at React Conf 2018](https://www.youtube.com/watch?v=dpw9EHDh2bM)
- Learned how to separate global application styles from individual component styling
- Organized the codebase into different component, container, and App directories
- Created an AWS Amplify User Pool to use with this React voting app and added the configs to the codebase
- Configured React Router and validated it worked as expected
- Attempted to write tests, but was surprised to hit an issue with testing the Hooks library I had used, so tabled this. 
- Sent test emails from SES and they worked, so that's nice. Not sure why I had such trouble the other day.

**Thoughts:** React app is getting all organized and configured! Today was a nice mix of learning and accomplishing things. At this point, I'm stepping through all the appropriate configurations to make for a client-side application: How can this be tested, how can styles be organized, how do I want to organize things, how do I handle configs, etc. . The only question of those that I punted on was writing tests. I bumped into an issue where Jest didn't understand the export syntax the custom hook was using. I don't know why this was. It was able to understand the same syntax from other components. When I attempted to add the configs to fix things to the package.json, Create React App let me know that particular Jest configuration was not allowed to be managed unless I ejected my React application from Create React App's configs. I'm not ready to do that because I don't want to mess with build tooling configs too much. This app is for validating I can build a thing that uses AWS Amplify, Cognito, SQS, and DynamoDB to handle global scale writes. I'd rather get through this client-side application portion ASAP in favor of the architecture work. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- Start incorporating AWS Amplify UI components using React Router to configure the proper redirects
- Figure out how to write test for a React app that uses Hooks
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 34](#day-34)
#### May 26th, 2019
**Today's Progress**:
- Wrote a simple application that manages application state using hooks

**Thoughts:** Set up a React app that manages application state using hooks and started building out the features! The React applications I've worked with before generally have used Redux to manage application state. Hooks has been a React feature on the periphery of my dev life for some time now. It felt appropriate to have a closer look at the feature as a state management alternative.

Working with Hooks to manage application state has been fairly straightforward with the assistance of [the use-global-hook npm module](https://www.npmjs.com/package/use-global-hook) described by its author in [this blog post](https://medium.com/javascript-in-plain-english/state-management-with-react-hooks-no-redux-or-context-api-8b3035ceecf8). Technically, I understand the module as a custom hook that handles updating a global state object. I have to give the blog a reread to make sure I understand it fully; I did notice some parallels to how Redux handles updating the state.  

However, I started having trouble debugging some basics at one point. It ended up I had messed up a destructuring assignment, but I realized I wasn't able to view the entire application state object. Redux had the ability to incorporate middleware for handling different cases. I'll probably end up writing my own middleware to give myself the tooling I need if it's not around for hooks yet. I'll want to keep the time I spend on that to a minimum, but I remember Dan Abramov encouraging that approach a few years ago in a podcast. It will be a good learning exercise. Tomorrow should be fun; Features all day on this basic React voting application! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 33](#day-33)
#### May 24th, 2019
**Today's Progress**:
- Worked through debugging the email situation more
- Wrapped up the tutorial after switching Cognito configs to send email instead of SES
- Began working on a voting app React front-end for an AWS Tutorial
- Read about using Hooks to manage State in React. I'm not sure whether to use Hooks or pull in Redux.

**Thoughts:** Started on a React voting app! I don't plan to turn this into an actual SaaS product. It will be part of a course on handling lots of data at once using AWS SQS and DynamoDB. I figured I'd get started on this while the work with AWS Amplify and AWS Cognito is fresh. 

I'm still not sure why SES wasn't sending emails. I did alter some configurations; Somehow the gmail.com domain was attempting to be verified on SES. I don't remember doing this and I clearly don't have acceess to gmail.com's DNS records, so I removed that. My hope was that was the reason SES wasn't sending emails. It could be part of the problem, but it didn't resolve the situation. The emails were still showing as being delivered, then I wouldn't recieve an email in my inbox. 

Switching the Cognito configuration to send from Cognito's emailing service instead allowed me to receive a verification email. It's nice to know my gmail account can receive emails; So it's not anything there. Later in the tutorial when I should've received another email I didn't. I ended up watching the last ten minutes of the tutorial as I guessed it would be pretty much the same AWS Amplify API calls as I'd already seen in the tutorial. It was, and I moved on.

Getting a feel for using AWS Amplify in a React application was something I didn't realize I'd have to do, but is absolutely essential. Looking forward to getting an initial cut of this voting application codebase together! I expect I'll end up configuring some sort of React app state management (possibly using Hooks), React Router, and AWS Amplify integrations for authentication. At that point I'll get to revisit the SES emailing situation again. Stay tuned! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 32](#day-32)
#### May 23rd, 2019
**Today's Progress**:
- Continued following a Youtube tutorial in using The AWS Amplify Authentication API to integrate with AWS Cognito User Pools
- Bumped into an issue with AWS SES "delivering" but then not receiving to emails to my email accounts

**Thoughts:** Working through an issue with AWS SES "delivering" emails, but then those emails are not received that's blocking wrapping up the Cognito tutorial; Yay debug day! The [Cloud Path tutorials](https://www.youtube.com/channel/UCTJxrTdQWFGtKxTeincy9uA) are going well as I wrap up Part 3 of their AWS Cognito tutorial. I reached a blocker in following through with the rest of the tutorial when AWS SES was delivering emails, but I wasn't receiving them at the verified gmail address I'm using with AWS SES. After learning a bit about DKIM and reading some SES docs I figured submitted a support ticket was a reasonable step. This seems like a common situation. I remembered this email was also configured to send emails under a different AWS account (an old work account), so wires could be getting crossed on AWS's side. I'm enjoying these tutorials because it has been a good review of writing a React application while teaching me AWS Cognito. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 31](#day-31)
#### May 22nd, 2019
**Today's Progress**:
- Followed a Youtube tutorial in using The AWS Amplify Authentication API to integrate with AWS Cognito User Pools

**Thoughts:** Followed 2 of the 3 Cloud Path YouTube tutorial videos on configuring a React front-end with AWS Cognito using AWS Amplify! So neat; I'm blown away that I hadn't used AWS Amplify before. As far as I've seen from the authentication API it abstracts so much complexity away when interacting with AWS's services. Since React is my client-side view library of choice these days, AWS Amplify is without a doubt a ridiculously useful asset. 

These [Cloud Path tutorials](https://www.youtube.com/channel/UCTJxrTdQWFGtKxTeincy9uA) are great! The author speaks clearly and attempts to keep things concise while delivering working results. Occasionally there's minor debugging of errors, which could get cleaned up, but the bit of debugging is helpful to see at times. I watched them at 1.5x speed and it was still really easy to understand. Onto Part 3 of this YouTube tutorial tomorrow! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 30](#day-30)
#### May 21st, 2019
**Today's Progress**:
- Finished configuring an AWS User Pool through the console

**Thoughts:** Getting a handle on AWS Cognito! Finished stepping through configuring a User Pool. It's pretty straightforward, and could be done pretty quickly, but I took the time to understand all the configurations and how to replicate the same configuration in a CloudFormation template. Interestingly, there is a gap or two between the console configuration and what's available in the CloudFormation API. Most notably, [the Verification Type can't be set to "Link" using CloudFormation](https://stackoverflow.com/a/48630404/5935694). 

After configuring the Pool I realized I don't really know how to use it with a codebase. There are several videos online describing how to do this. I made a YouTube playlist of them. Between this update and the next I'll absorb enough from those videos to start building my own demo app and prove I can use the Cognito User Pool as it's meant to be used. Good stuff! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 29](#day-29)
#### May 20th, 2019
**Today's Progress**:
- Dug into AWS Cognito

**Thoughts:** Dug into AWS Cognito! One of the practice questions when studying for the AWS Solutions Architect - Professional exam was around creating an online voting solution. It's one of the systems that, from a client-side perspective, is a straightforward CRUD app. However, scaling to handle the load and building reports off the data in real-time requires an appropriate architecture. Clearly, one would want to maintain the integrity of the initial vote, so AWS Cognito or some other indentification solution is essential. 

I'm pretty excited about the approach I took to dive into AWS Cognito! Instead of stepping through the web console using its wizard, I opened up the AWS Cognito CloudFormation documentation and began writing a CloudFormation script as I walked through the web console. Once I've stepped completely through the web console, I should also have a CloudFormation script that should generate the exact same configuration as I had selected in the web console! I can test the two configurations in the same way, resolve any differences, then work from the CloudFormation script going forward! It could be handy to approach other services this way as well, including the ones I already know. 

With a family wedding over the weekend I missed three days in a row -- BAD! But good that I was present with my family. I'm confident I made the right choices; Have to get back on track and not miss any more days consecutively! With no family or travel plans until I am done with my 100 days my excuses can only get worse. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow-ish** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 28](#day-28)
#### May 16th, 2019
**Today's Progress**:
- Assessed [groundedit.solutions](https://groundedit.solutions) using Google Chrome's audit tools 
- Addressed an issue with groundedit.solutions a friend pointed out
- Learned about CloudFront caching! 

**Thoughts:** Resolved a UX issue with website I'd recently published! When making network calls through experience & internet advice I've learned there end up being three states: The request has not been sent, the request has been sent, and the results of the request have been received. I'm treating receiving the event as its own cascade of results. 

When I put together [Grounded IT Solutions](https://groundedit.solutions) I didn't adequately account for the user experience while the network request was being sent. A friend of mine was using our local subway; When she pressed submit she didn't see any response from the UI, then waited for something to happen. Apparently, the network request must have had issues being sent while on the subway (a common phenomenon), so she didn't see the website work as expected. A bug, yay!! In this case the network request probably hung, waiting for a resolution; While that was happening the UI didn't update. So today I resolved that! 

A simple way to do this is to replace the element being pressed with something indicating action is occurring, like a loading icon. I can't critique much because I just messed up this UI situation, but, honestly, it would be great if websites would indicate the progress of processing a particular network request. There isn't any processing here; Just an indication that the individual's email was successfully resolved, so I didn't think through handling the case where the network request itself didn't respond within a few seconds. My friend must have clicked the submit button, lost network access, which caused the webpage to wait on the default network timeouts (usually much longer than three seconds, the standard for giving user feedback I've heard of), and, from her perspective, the website's submit button didn't work at all! Not a great look for a new IT company. When using American Airlines website later this evening I noticed the same situation occurring, so I didn't feel that bad. There's still a place my IT company can help out :-) .

When deploying this update I learned CloudFront defaults to caching distributions for 24 hours. This would mean that users of my website wouldn't see any UX updates for 24 hours?! That's not ideal, so I updated the distribution to refresh itself every hour, with a day being the longest amount of time it should take to refresh from edge locations. So within a day all users should see the ideal behavior. It's worth noting that I'd be fine serving this website from an S3 bucket from the Northern Virginia region taking the global latency in stride, but in order to serve the files over HTTPS I had to associate a certificate with a CloudFront distribution! It would be neat if AWS provided a way to enable HTTPS on S3 buckets for static websites. I could be missing something though as this seems like a pretty straightforward feature to provide.

I have a wedding this weekend; I'm thinking I can continue with my 100 days of code/cloud tomorrow, but Saturday, the day of the wedding, will probably end up being a day off. We'll see! Back to the regular schedule on Monday at the latest. 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 27](#day-27)
#### May 15th, 2019
**Today's Progress**:
- 20 more questions to study for the AWS DevOps Engineer Professional Certfication
- Read Gartner's Magic Quadrant report for Cloud Infrastructure as a Service, Worldwide (i.e. IAAS offerings)

**Thoughts:** Dove deep into the [Gartner's 2018 Magic Quadrant for, effectively, IAAS offerings](https://pages.awscloud.com/gartner-2018-cloud-IaaS.html?trk=ar_card)! Recently, when I've described the content of the courses I'll be putting together to other IT professionals/friends there's typically some comment as to the relative success of the different services being discuss in the course. Understanding that each service offering for any company will have success relative to it's competitors, I felt I needed to get a handle on this myself. 

The broadest assessment is comparing IAAS offerings as a whole across cloud providers. I've leaned on Gartner's Magic Quadrant before to orient my opinions, and this report didn't disappoint. Conversationally, people toss around comments like, "Alibaba is going to be big", "Azure is catching up to AWS", or "You should really check out GCP". These comments are well-meaning, but in a big world of online content marketing noise and office/contract/company echochambers it's important to cut straight to the professionals paid to digest it all and voice thought out opinions. 

Note that I'm open to learning about these different Cloud Providers and heir offerings; Starting with AWS will give me the context to understand the technical aspects, then comparing that to other Cloud Providers will significantly accelerate my understanding. This report is a year old and expected to be updated this month. It provided me a snapshot in time view of a state of Cloud Providers. It seems Alibaba has been leveraging its Chinese offerings to provide international offerings, IBM & Oracle have significant IAAS projects slated to enhance and harden their IAAS offerings, Google has been refactoring internal systems as IAAS services to bootstrap their offerings, Microsoft is determined but dealing with the pains of growing fast, and AWS is still, hands-down, the market leader in services and ability to execute. 

Reading a report that's a year old is, on the surface, not a great use of time, but I'd argue it provides a reference point to judge the changes to the 2019 report. Now I'm excited for the updated report that should be published this month. I'll be able to see the evolution of different Cloud Providers over the past year, presuming they all will still be included in the report! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 26](#day-26)
#### May 14th, 2019
**Today's Progress**:
- 20 more questions to study for the AWS DevOps Engineer Professional Certfication
- Figured out my tech vision for the next six months 

**Thoughts:** Completed 20 more questions studying for the AWS DevOps Engineer Professional Certification and recentered myself after getting [Grounded IT Solutions brochure site](https://groundedit.solutions) set up how I wanted! Sitting down today I realized I wasn't completely clear with myself on what I wanted to do for the next six months. I knew I would do 100 days of code/cloud, but what for Grounded IT Solutions and earning some revenue? After a refill of [corsica](https://www.lacolombe.com/products/corsica) and a few hours brainstorming I landed on continuing to pursue the AWS DevOps Engineer Professional Certification and releasing one Udemy course a month, starting August 1st, until the end of 2019 (well, technically the last one would be released by January 1st). I should start 2020 with six Udemy courses on AWS stuff and two AWS Professional-level certs to my name! Not a bad 2019 for sure!

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 

**Tomorrow** 
- Write client side using GatsbyJS
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 25](#day-25)
#### May 13th, 2019
**Today's Progress**:
- Styled a brochure site for my new company
- Deployed the brochure site as a static site on S3
- Configured a custom domain for the API Gateway so that I can send requests to api.groundedit.solutions/v#/whatever
- Configured a CloudFront distribution so I can serve the brochure site over HTTPS. It's necessary as I'm collecting interested parties emails. 

**Thoughts:** Website is live! It's a GatsbyJS client-side served via CloudFront & S3 with an API Gateway API that kicks off a Lambda function that updates a Google Sheet! After missing a few days due to life stuff I wanted to get this website posted today. I had an enjoyable time styling the site, then got strung along as it took a little more than expected to configure S3 bucket to be served from HTTPS. When I got into it I figured it would be configuring S3 to use a public certificate from AWS Certificate Manager. It turns out this has to be configured through CloudFront. Changes to a CloudFront distribution can take up to 20 minutes to take effect, so I found myself making a change to the CloudFront distribution's settings, waiting about 15 minutes for it to deploy, then testing it, rinse and repeat. Lengthy iteration time for sure! This would absolutely be something to consider if debugging a live CloudFront distribution where a CloudFront config was preventing content from being accessed. Clearly, that would be no good. 

One great thing I learned is that public certificates are free via Certificate Manager and they refresh themselves! Aleviating the concern of HTTPS certificates expiring with no additional cost was a breath of fresh air for sure. 

Looking forward to tomorrow! I'll send this website around to friends and family to ensure it works on their devices, then get back to focusing on getting the AWS DevOps Engineer Professional cert! I want to double-up my studying so I get that credential sooner rather than later and can move on to bigger and better things. Onward and upward! 

**Link to work:**
- [Grounded IT Solutions website is live!](https://groundedit.solutions) 
- Nothing for today...but coming soon! 

**Tomorrow** 
- Write client side using GatsbyJS
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 24](#day-24)
#### May 9th, 2019
**Today's Progress**:
- Poked around React's documentation covering gaps in my understanding and confirming best practices (Parcel, Next.js, styling, and ajax calls)
- Continued working on a website using GatsbyJS. Learned more about GatsbyJS's set up and ecosystem. 

**Thoughts:** Getting a handle of GatsbyJS and the client-side is coming together! When initially working with GatsbyJS I was feeling a little confused. I haven't written React consistently for awhile now, worked with GraphQL, or used some of the build tooling I was stumbling across. So I took a step back and started looking through React's and GatsbyJS's docs. Once I had those gaps filled and began browsing the codebase again my thoughts were coalescing and results started flowing. By the end of my time working on this today the client-side is really starting to come together and look halfway decent for a placeholder, "coming soon" style site. 

**Link to work:** 
- Nothing for today...but coming soon! 

**Tomorrow** 
- Write client side using GatsbyJS
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 23](#day-23)
#### May 8th, 2019
**Today's Progress**:
- Deployed a test API endpoint using API Gateway
- Wired up a simple form to the api and validated I could submit a value through the form that gets stored in the Google spreadsheet

**Thoughts:** Wired up simple client with the API! Pretty straightforward day refactoring a React form to post the form data to the API I've been setting up the past few days. Now the whole flow is complete: A user will be able to visit my website, submit their email, then that email will be sent to an API endpoint that kicks off a Lambda function that appends the email to a list of emails in a Google spreadsheet. Google Sheets will then notify me that someone has added their email. 

I guess this is technically my first "serverless" application. I wanted a custom front-end that could be served as a static file, I wanted to be able to collect leads of folks interested in my company, and I wanted the whole set up to be as cheap and robust as possible. As the company will be regional in nature and quite small, I don't expect much activity. Having a server deployed and running 24 hours a day is not really worth it. This is where using Lambda makes sense. I doubt I'll accrue more traffic than API Gateway and Lambda's free tiers, so, practically speaking, the back-end of my website is free! That's worth a chuckle. Since the front-end is just a lightweight static file I expect load times will be very quick. Not a bad approach for a company promoting pragmatic IT solutions! 

Next steps are making the website attractive, professional, lightweight, and maintainable. That should take the weekend, so expect a link soon! 

**Link to work:** 
- Nothing for today...but coming soon! 

**Tomorrow** 
- Write client side using GatsbyJS
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 22](#day-22)
#### May 7th, 2019
**Today's Progress**:
- Wrapped up configuring "server-side" setup with API Gateway kicking off a Lambda function to store form data!

**Thoughts:** Finished configuring API Gateway and Lambda to handle form data! I was getting a bit frustrated because it was taking too long to get into a Node.js coding groove. Things finally started clicking today. It felt like a matter of shaking the rust off as it has been several weeks since I've had head down coding sessions. Next up is writing the client side landing page; Looking forward to getting my hands dirty with GatsbyJS! 

**Link to work:** 
- Nothing for today...but coming soon! 

**Tomorrow** 
- Write client side using GatsbyJS
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 21](#day-21)
#### May 6th, 2019
**Today's Progress**:
- Looked into AWS SAM (Serverless Application Model), and installed the local tooling
- Iterating over my Lambda function for storing data in a Google sheet

**Thoughts:** Learning about how to handle builds with Lambda! I do have a development flow going, but it involves writing code locally, creating a .zip file, uploading the .zip file via AWS's Lambda console, identifying a local file to use as the test HTTP request in vscode (every time), then testing the Lambda function! 

I'm definitely missing something in my build flow; A close friend mentioned that I should be running everything locally. I did install SAM, though it's possible I'm not using it properly. I am definitely running the Lambda function that's hosted on AWS, but, based on what I learned today, SAM is supposed to test everything locally in docker containers. This is desireable as I'm currently adding to my Lambda request count in order to iterate over my Lambda code. This clearly counts towards my overall costs, though the first 1 million Lambda requests are free. I presume it wouldn't do this if I was able to test my Lambda code on my local machine. If I hit 1 million Lambda requests this month cheers to me because that means I'm popular for some reason (or bots) :-) . 

**Link to work:** 
- Nothing for today...but coming soon! 

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.
- Upgrade primary driver to Ubuntu 19.04

### [Day 19 and 20](#day-19-and-20)
#### May 4th & 5th, 2019
**Today's Progress**:
- Introduced myself to AWS's API Gateway to set up API endpoints that can kick off Lambda functions. Successfully connected the two, next is getting the Lambda function to consume the data from the POST request and do the right thing with the submitted data. 
- Continued wiring up an email component with a lambda function that would then post to Google Sheets to capture emails of folks interested in getting updates about my LLC

**Thoughts:** Making some progress setting up an API that kicks off a Lambda function! Today and yesterday mostly consisted of ironing out the wrinkles in my development and deployment of my first Lambda function. Tomorrow will be working through integration issues iterating over the code I'd like to work with my Lambda function. 

Another hurdle I will have to overcome is setting up my API to use HTTPS. It looks like that will mean deploying an API behind a Network Load Balancer in a VPC. It should be no big deal, but it is more overhead to getting this feature deployed. I wouldn't deploy it without this level of security, so it has got to happen. Fortunately, I enjoy the work, so looking forward to setting it up! 

**Link to work:** 
- Nothing for today...but coming soon! 

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 18](#day-18)
#### May 3rd, 2019
**Today's Progress**:
- Continued wiring up an email component with a lambda function that would then post to Google Sheets to capture emails of folks interested in getting updates about my LLC

**Thoughts:** One of those days where I read something wrong then overcomplicated things, but now I understand JSON Web Tokens way better than I did before! Some simple node code is reading values from Google Sheets; Tomorrow is switching that to be writes, append a value, deploy it AWS Lambda, then wire up the client to the Lambda. Good stuff! 

Yesterday I created a Google service account to handle communicating between AWS Lambda and Google's API. That generates an email associated with the service account. Adding the permission for the service account to read from the spreadsheet was done by granted the service account permissions through the Google Sheets interface, as if I were sharing a private document with a friend using their email. 

I found this intermingling of interfaces to add permissions for a service account through the actual Sheets web application kind of surprising. AWS and Amazon.com have a natural segmentation with selling products versus using web services. The AWS interface has no need to interoperate via the Amazon.com interface. But, I guess, since Google's long-term business has been selling web services (broadly speaking) it makes sense that some of their GUIs I was familiar with for different purposes now are being used for managing account permissions of integrations between web services. I found it surprising, like when someone you know well does something completely unexpected; "Mom, I didn't know you could do a backflip!!"

Continuing to work on this tomorrow! Either an early morning update or a late day update as I'm running an obstacle course race during the day!

**Link to work:** 
- Nothing for today...but coming soon! 

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 17](#day-17)
#### May 2nd, 2019
**Today's Progress**:
- Registered a domain for my LLC
- Got familiar with Gatsby JS and set up a development project
- Began wiring up an email component with a lambda function that would then post to Google Sheets to capture emails of folks interested in getting updates about my LLC

**Thoughts:** Finally took that breather from AWS DevOps Engineer questions to get started with a brochure site for my LLC! I gave Gatsby JS a look because, from what I understand about it, it has potential to set up a nice, simple workflow for customer's to alter a brochure WordPress site, then build it through Gatsby and deploy it on AWS as a static site (super cheap to maintain and globally performant). It seemed able to do this, so went through the super quick hello world and began refactoring that into my LLC's website. 

I'm not ready to accept contract work yet, so the website would end up being a nice looking landing page with an email form for general inquires. I thinking this through I figured it would be alright to start by writing these emails to a Google spreadsheet using Google's Sheets API proxied through a Node.js script on an AWS Lambda function. It would make it easy to port to data to another data store eventually and copy/paste those emails into a general update newsletter for those interested in the LLC whenever I wanted to give an update. 

The primary learning ended up being setting up a service account to use to authenticate the Lambda's request to Google's Sheets API. I don't love how Google's API and Cloud interface redirects around their different services. I'm not sure if I'm in a quickstart or in their identity and access management at times. The primary way to tell is by hovering over their side menu to see the title. Some links I clicked had me confused as to why I was directed places, but that's probably more due to my lack of familiarity with Google Cloud and their services. No better time to learn than the present! 

So today kind of stumbled into building a cross-Cloud service and a landing page. I don't want to spend more than a few days on this, but I don't think it will take more than a few days, if that. 

**Link to work:** 
- Nothing for today...but coming soon! 

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 16](#day-16)
#### May 1st, 2019
**Today's Progress**:
- Did another 20 practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Scored dropped a bit but I learned a bunch from the questions I got wrong. Such as: 
- Jumbo Frames are ethernet frames that handle more than 1500 bytes of data. I understand it as being able to send more data per packet. When setting up a high performance computing cluster on AWS [you can set the Maximum Transmission Unit setting on a linux box to upwards of 9000 bytes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/network_mtu.html#jumbo_frame_instances)! That's six times more data per packet! Neat! 
- EBS snapshots are actually stored on S3. So AWS's EC2 services can be up, but if your deployment scripts presume your EC2s will use an EBS volume and S3 is down, your deployment scripts will probably not work.

Good times! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 15](#day-15)
#### April 30th, 2019
**Today's Progress**:
- Did another 20 practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Similar score to yesterday! Things are coming together. Still learning new things. For example, the term "Dead Letter Queue" is a message queue that other queues send unsuccessfully processed messages for deep analysis. Using AWS Config might've been an option I could have used to generate a report of configuration changes made throughout a given period at my last job (maybe, I have to validate this one). Stuff like this! 

Still getting bored with just posting that I did more questions. But know that this is not the only iron in the fire :-) .  

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 14](#day-14)
#### April 29th, 2019
**Today's Progress**:
- Did another 20 practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Well, well, well! I scored 15% higher on my AWS DevOps Engineer questions today! Feeling pretty pleased, but I know it's prudent to temper myself. I'll have days where I drop by 15%, but I was due for some better results after doing about 100 questions so far. 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 13](#day-13)
#### April 27th and 28th, 2019
**Today's Progress**:
- Did another 20 practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Life had me on the move for the whole day yesterday. It was my first missed day so far. I got lots done, just not 100 days of code things. Hopefully it won't happen again! I'm ensuring I actually do 100 days by counting this as day 13, but accounting for the April 27th and 28th. 

Today I did another twenty practice questions. I'm definitely learning because I get more opinionated about the answers to the questions. At times, it can feel like something I've learned from previous questions contradicts what I learn from newer questions. Most of the time the explanation spells out the difference, but occasionally it doesn't. This can be frustrating, but I had this experience before prepping for the AWS Solutions Architect Professional exam. 

There have been several cases around handling log files for analysis given business requirements from several parties. This is a really neat and practical system, incorporating streaming aspects with analytics. It feels like a pretty common experience across architectures, and it's getting me excited to practice building such a ubiquitious OLTP to OLAP setup. The patterns here can be replicated across any sort of streaming data into an analytical, persistent data store. 

Questions like these have me longing for a time when I switch back to pragmatic drilling with AWS services. Actually getting the certification is pulling at my like a strong magnet, so I'll probably follow through, but, oh boy, it'll be a blast standing up the architectures I'm being asked about sometime during these 100 days! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 12](#day-12)
#### April 26th, 2019
**Today's Progress**:
- Did another 20 practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Another day of practice questions! A sign that I'm in the right field is a really enjoy doing these practice questions. Most of them are scenario-based, which puts me in a different mindset than I am typically in. At times the context they describe is broad enough where the approach in reality is subjective. The problem can be solved in several ways. When this happens, it's more an exercise in test-taking skills, giving the answer the question is asking for versus the answer that, in the real world, would probably be a fine solution. It's just not the solution that answer is looking for. It's usually between two answers (the others can be easily ruled out) so it's pretty easy to find the buzzwords that indicate the ideal answer. "Cost-effective", "real-time", "deploy quickly" point towards less resources & temporary, whatever answer references Kinesis, and whatever answer references Elastic Beanstalk, respectively. Nine times out of ten this works out.

It feels necessary to shed some light on how I am prepping for the AWS DevOps Engineer certification exam for context. I study best for tests with practice questions and answers. AWS doesn't publish exactly how many questions are on the AWS DevOps Engineer certification exam, but, assuming eighty over three hours like the Solutions Architect exams, taking two minutes per question allows one to finish the exam in the time alloted. I set a timer for ten minutes, then aim to complete five questions within that time. Afterwards, I set another timer for ten minutes to review my results and the answer's justifications from WhizLasdbs. This keeps me from surfing the web too long. The time pressure also keeps me focused. Something about racing against the clock puts me on edge in a good way. 

So if I do twenty questions in a day it means I spent about an hour and twenty minutes testing myself and reviewing content. It's easy just to blow through twenty questions, but the learning happens when reviewing the answers. An added bonus is I can assess my progress at any time. Currently, I'm hovering around getting 70% of the questions correct. Considering that's technically enough to get the certification and I'm early in my studying, I expect this number to rise. It's even more accurate because each question is one I haven't seen before. Once I get through the 400 questions I have from WhizLabs I'll have to start over with questions I've already seen, but by that time I should be averaging high enough to be confident in sitting for the exam. 

This way of studying only works if it fits the exam format and I can get a significant cache of questions with answers and answer justifications, but when those pieces come together this is a super effective way of learning for me. However, it's definitely learning just to get the paper; Practically applying what the questions are asking makes the certification actually worth something. In the near term I think I'll keep going with these practice questions, but spend time doing something else not necessarily AWS-related that I wanted to learn during my 100 days of code. Then, in about twenty days when I finished the four hundred questions, I'll probably sit for the exam, then get back to experiential learning versus book-learning. 

Posting early today because I'm seeing Avengers: Endgame at 1130am and I bet I won't be interested in working after that :-) . Happy weekend!

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 11](#day-11)
#### April 25th, 2019
**Today's Progress**:
- Did 20 more practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Life is preventing me from keeping the pace I want with 100 days of code things, but my days should get more focused next week. A validating aspect of this studying is I'm getting enough questions correct that I'm actually getting a passing score in aggregate! It's barely passing, but I'm glad my workplace experience, general interest, and other certification studying is overlapping. 

A few days ago I listened to a Packet Pushers podcast that disagreed with creating modular Terraform scripts. Interestingly enough, there was a practice question that implied CloudFormation's nested stacks should be used to delegate out responsibilities of different portions of an architecture to other teams in an organization! That makes sense, but I can understand the concern of the individuals on Packet Pushers. There would have to be some harmony between other team's making changes and overall application oversight of those changes and how they're applied. My gut reaction is I'd rather have individual teams responsible for their whole CloudFormation scripts, with a library of nested stacks created by security/web tier/database experts in the organization they can reference. On occasion, the appropriate expert could audit the related portion of the CloudFormation template to assess how the team is handling, say, security, based on the organization's internal recommendations. Something like that, maybe. The VPC they deploy to should probably be an overarching, default stack whether the application is internally or externally facing, but that's it. 

Tomorrow will be another day of AWS DevOps Engineer questions. That will happen in the morning, then seeing Avengers Endgame in the early afternoon! Happy Friday! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 10](#day-10)
#### April 24th, 2019
**Today's Progress**:
- Read through the [different validation errors](https://aws.amazon.com/premiumsupport/knowledge-center/cloudformation-template-validation/) to happen so I can recognize them quickly in the future
- Did some practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Looks like studying to be a Certified DevOps Engineer is the natural next step! In assessing my ambitions compared with my original plan for the 100 days of code, I found that I wanted to solidify my knowledge deploying codebases in an automated way. The thing I'm not sure about yet is handling application-level configurations. I've done this in the workplace using Jenkins Pipelines, but I want to ensure this is the "AWSy way" to do things. That had me browsing the AWS DevOps Engineer certification page. 

It was ridiculous how nearly every domain the exam covers is what I'm interested in learning! There were several reasons why I didn't review the exam criteria much previously, not the least of which being I didn't want to use my 100 days of code to get certifications in lieu of practically applying whatever the acumen the certification was supposed to test for. I value practical experience over paper. But the act of studying for the DevOps Engineer certification should point me in the direction of the best practices. Later, I can exercise implementing those best practices. 

Nothing really to say about reading through the validation errors. They're pretty standard and what you'd expect. Looking forward to running through more practice questions tomorrow for the AWS DevOps Engineer certification! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Do some practice questions for the AWS Certified DevOps Engineer - Professional exam
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 9](#day-9)
#### April 23rd, 2019
**Today's Progress**:
- Continue reading Patterns of Enterprise Application Architecture
- Listened to [a podcast about Curt Micol's experience with Terraform](https://player.fm/series/packet-pushers-full-podcast-feed-1402332/full-stack-journey-027-understanding-infrastructure-as-code-and-terraform-with-curt-micol)

**Thoughts:** Life this week has me in a car or, at the very least, out of a chair, so I had to find ways to continue fulfilling the 100 days of code challenge. [Packet Pushers podcast](https://player.fm/series/packet-pushers-full-podcast-feed-1402332) had an episode dedicated to Curt Micol's experience with Terraform. This was a fantastic episode; I love a pragmatic assessment of leading edge technologies, and this podcast delivered on that. 

Curt brought up the idea of "Defensive Terraform". I've only listened to the podcast once through, but what I gathered is that once a Terraform script is run it's difficult to tie the infrastructure changes to future "runs" of that Terraform script. If any changes to the infrastructure that was created had occurred Terraform would stop the execution of its current build. I find this strange; I think CloudFormation has a feature to detect, what AWS calls, "drift" in CloudFormation templates. It makes sense that, if there is a GUI to alter infrastructure, that GUI could be used and an infrastructure-as-code offering should account for that. 

The "Defensive Terraform" idea comes from a place where editing one's Terraform scripts could result in consternation throughout the team if someone else were working on or using that Terraform script. This was resolved, I think, by hashing each Terraform script when it was changed, then naming the script with that hash (?maybe?). If that hash had changed, then a different script was being run that expected, and the Terraform script would abort. 

Honestly, this feels heavy handed to me. I'm fascinated by Terraform. AWS is what I'm familiar with, so it was natural and convenient to pursue CloudFormation during my 100 days of code, but I expected I would attempt the same results with Terraform at some point. I think AWS solves this by detecting drift in different CloudFormation Stacks, then only changing the infrastructure where the Stack differs from the existing infrastructure. 

By extension Curt does not agree with applying a "modular" approach to infrastructure-as-code. This was a primary tenant of my interest in CloudFormation. I think there is fantastic potential in having a static web server template that all applications use, with the ability to sprinkle their application-specific configurations into the template. CloudFormation could provide this (with an abstraction where needed), but Curt's objection was something along the lines of different teams altering their own infrastructure-as-code scripts could cause breakages in other team's scripts. This makes it ideal to edit one script as a whole. 

Definitely listen to the podcast and come up with your own opinions! I've only listened to it once; Most insightful podcasts I listen to several times, and this is one of those podcasts for sure!

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Force the [different validation errors](https://aws.amazon.com/premiumsupport/knowledge-center/cloudformation-template-validation/) to happen so I can recognize them quickly in the future
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 8](#day-8)
#### April 22nd, 2019
**Today's Progress**:
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- Continue reading Patterns of Enterprise Application Architecture

**Thoughts:** Life ended up making this a lighter day as far as 100 days of code activities go. However, correctly matched 31 definitions in a row! Getting better recognizing the Patterns of Enterprise Application Architecture terms! Then began working my way through the introduction and Part 1: Narratives. While reading a phrase "These are my people" popped into my head as I thought of any other IT professional who had read this textbook. That validated reading Patterns of Enterprise Application Architecture as a fruitful activity! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Force the [different validation errors](https://aws.amazon.com/premiumsupport/knowledge-center/cloudformation-template-validation/) to happen so I can recognize them quickly in the future
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 7](#day-7)
#### April 21st, 2019
**Today's Progress**:
- Created and played a private sporcle to learn the list of patterns in [Martin Fowler's Patterns of Enterprise Application Architecture](https://www.martinfowler.com/books/eaa.html)

**Thoughts:** Today took a left turn when it crossed my mind to finally crack open Patterns of Enterprise Application Architecture by Martin Fowler. My brother gave it to me for Christmas. After browsing the table of contents I opted to create some way of memorizing the most glossary-like section of the book, the "List of Patterns". Where an author typically takes a few paragraphs or more to explain something, the glossary forces them to put it in the most concise language possible. Starting with the glossary does add complexity and can seem ambiguous, but it allows the actual textbook reading to provide clarity to the definitions. I like figuring out how the author distilled down to the definition, instead of attempting to distill down to my own definition while reading, then using the glossary as a reference, where the definition could confuse me more if the definition I created in my mind doesn't closely resemble the definition the author came up with. 

I created a sporcle of the definitions; It ended up being a great way to gamify the learning! I tweaked the rules and ended up landing on a minesweeper type game, where any wrong answer would end the game. When I lost I could reference the book. I think my longest streak was nine in a row out of fifty-one. Not bad for the first day, I think! The sporcle is still in draft because I can't figure out how to show the user the correct answer on the one they got wrong. It doesn't seem to be in the game configurations, unfortunately. I'm looking forward to incorporating fifteen minutes of this sporcle into my morning routine until I'm acing it! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- 15 minutes of the Patterns of Enterprise Application Architecture sporcle
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Force the [different validation errors](https://aws.amazon.com/premiumsupport/knowledge-center/cloudformation-template-validation/) to happen so I can recognize them quickly in the future
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 6](#day-6)
#### April 20th, 2019
**Today's Progress**:
- Import an EC2 into a VPC CloudFormation template, deploy it, and test it works as expected (SSH & HTTP). Yay modular CloudFormation templates!

**Thoughts:** Yay! Nested import of an Internet Gateway is working! The trick was using the GetAtt intrinsic function to reference the Internet Gateway. When the resource is within the same CloudFormation template, it seems properties of a resource type can be referenced by referencing the resource in the template. Note how the "GatewayId" property is referenced in... 

...this (nested stack)...
```yaml
  Route:
    Type: AWS::EC2::Route
    DependsOn: AttachGateway
    Properties:
      RouteTableId:
        Ref: RouteTable
      DestinationCidrBlock: 0.0.0.0/0
      GatewayId: !GetAtt InternetGateway.Outputs.InternetGateway
```

...versus this (same template)...
```yaml
  Route:
    Type: AWS::EC2::Route
    DependsOn: AttachGateway
    Properties:
      RouteTableId:
        Ref: RouteTable
      DestinationCidrBlock: 0.0.0.0/0
      GatewayId:
        Ref: InternetGateway
```

I'm not 100% convinced I completely understand this, but at least I realize there is a difference here that can trip things up. I think it has something to do with referencing blocks of yaml in the same file versus referencing blocks of yaml via a nested stack output. 93+ more days to figure it out! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Force the [different validation errors](https://aws.amazon.com/premiumsupport/knowledge-center/cloudformation-template-validation/) to happen so I can recognize them quickly in the future
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 5](#day-5)
#### April 19th, 2019
**Today's Progress**:
- (In Progress) Import an EC2 into a VPC CloudFormation template, deploy it, and test it works as expected (SSH & HTTP). Yay modular CloudFormation templates!

**Thoughts:** So close! Currently one CloudFormation template of an Internet Gateway is successfully being imported (i.e. a "nested stack", as I understand it) into another CloudFormation template that creates a VPC, EC2, and wires the things up. I chose an Internet Gateway as my first import because it doesn't have many parameters to map. When I run the parent template it fails because it thinks the Internet Gateway doesn't exist in the Attach Gateway step (i.e. resource type). Obviously, they're related. I'm sure the imported template is being imported because CloudFormation creates a stack for it in the console. However, I suppose the Attach Gateway resource type isn't being associated with the Internet Gateway. Tomorrow's first step is going to be porting the Attach Gateway resource type into the Internet Gateway imported template, which will require updating the parameters to include the VPC. Hopefully that resolves the situation! I wonder if certain resource types need to be grouped together in nested stacks; Hmmmm... to be continued tomorrow! P.S. This [AWS sample github repo was super helpful for getting my arms around importing templates into other templates](https://github.com/aws-samples/ecs-refarch-cloudformation)! 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Force the [different validation errors](https://aws.amazon.com/premiumsupport/knowledge-center/cloudformation-template-validation/) to happen so I can recognize them quickly in the future
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 4](#day-4)
#### April 18th, 2019
**Today's Progress**:
- Opened an issue with Algo asking about configuring Ubuntu 18.04 desktop machines to use the Algo VPN server
- Spun up an EC2 in a VPC with CloudFormation, SSHed into it, and loaded a webpage on port 80

**Thoughts:** Oh! Feeling awesome! Deployed my first CloudFormation template using the AWS CLI! What I'm most happy about though is I read through the template to ensure I understood the resources being spun up, the purpose of the different portions of the template, and how they interact together. The AWS Solutions Architect certifications I have really helped with the "Why do I need this block of yaml?" etc. . I made sure to learn how to validate the template, and it worked the first time, which was great. I learned some peripheral things as well from the different AWS CloudFormation configurations, such as a [different way for expressing time passed](https://en.wikipedia.org/wiki/ISO_8601#Durations). 

Earlier in the day I had [commented on an Algo issue](https://github.com/trailofbits/algo/issues/1021#issuecomment-484512823) linking to the blog post I had used instead of their documentation. Turns out there is an Algo doc already for doing the same WireGuard configuration as was in the blog post! Glad to see my circumstance was already covered, and it was great to get a response so quick pointing me to the appropriate place in their docs. 

**Link to work:** 
- Nothing for today

**Tomorrow** 
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Import an EC2 into a VPC CloudFormation template, deploy it, and test it works as expected (SSH & HTTP). Yay modular CloudFormation templates!
- Force the [different validation errors](https://aws.amazon.com/premiumsupport/knowledge-center/cloudformation-template-validation/) to happen so I can recognize them quickly in the future
- I'm not seeing my CloudFormation events in CloudTrail, just an AssumeRole, and things happen. I want to know why this is.

### [Day 3](#day-3)
#### April 17th, 2019
**Today's Progress**:
- Stood up an Algo VPN server and connected to it

**Thoughts:** Whoa! Today took quite a diversion from my plans yesterday. I woke up feeling anxiety about life stuff I ignored debugging the VPC configuration issue yesterday. Thinking about where I'd do that work, I realized I didn't have a VPN server configured to work with my personal laptop. That meant I was confined to working in my apartment until I could secure my traffic somewhere besides my apartment. So I bumped off the plans from yesterday and instead used [Algo](https://github.com/trailofbits/algo) to spin up a VPN server on AWS. What ended up being the issue is configuring my Ubuntu 18.04 machine as the client to connect to the Algo server. After the instructions in the Algo docs weren't working out for me I just googled it. Following [this blog post](https://computingforgeeks.com/connecting-to-algo-vpn-server-from-linux-and-android-devices/) to set up a [wireguard VPN tunnel](https://www.wireguard.com/) worked out well! Then I went to the coffee shop and spent several hours sorting out the rest of my life besides the 100 days of code. It feels great to be able to work from somewhere besides my apartment now that I have my own VPN server to secure my traffic. Back to CloudFormation tomorrow! 

**Link to work:** 
- Nothing for today

**Tomorrow** (adding this because it keeps me organized and motivated)
- Open an issue with Algo asking about configuring Ubuntu 18.04 desktop machines to use the Algo VPN server
- Spin up an EC2 in a VPC, SSH into it, and load a webpage on port 80
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Import an EC2 into a VPC CloudFormation template, deploy it, and test it works as expected (SSH & HTTP). Yay modular CloudFormation templates!

### [Day 2](#day-2)
#### April 16th, 2019
**Today's Progress**: 
- Started refactoring a sample EC2 in a VPC CloudFormation template
- Debugged what turned out to be a configuration issue SSHing into the EC2

**Thoughts:** Today started with reading articles about CloudFormation to procrastinate failing at using CloudFormation. I do that sometimes. Once I got to refactoring an example Cloudformation template the editor updates from yesterday shined! It was really easy to navigate the CloudFormation template and the linting caught several issues that would've been tedious and time consuming to iterate through later. The day took a turn for debugging (i.e. the worse) when I tried to validate I could SSH into an EC2 with the key pair I'd use in the CloudFormation template. Turns out something was off with the default VPC I had that was spun up with a sample CloudFormation script a week ago. Then I had noticed something was funny about this VPC, but I dropped the issue because I had other work stuff to do. In debugging, I learned a bit about identifying SSH keys and validating which pem file the EC2 expects without using the AWS console. I also learned that ubuntu 18.04 doesn't have an SSH service running by default. As expected, that's caused some surprise for folks that upgraded their Ubuntu servers from 16.xx to 18.04 and weren't able to log into them again. Honestly, still not sure how they fixed that without being able to log in and start the SSH service. I digress; My issue ended up being adding an internet gateway to the route table. I thought if I attached the internet gateway to the VPC that would handle routing to the subnets. Also, the VPC flow logs indicated my SSH traffic was accepted, which made me think it was being routed successfully to the server. That deflection made me chase lots of red herrings. I even checked to see if my ISP was blocking port 22! Oh well, I'm able to successfully log in :-) . Tomorrow I'll turn off my SSH service on my Ubuntu 18.04 machine and see if SSH fails. For now, I'm good. What a day! 

**Link to work:** 
- Nothing for today

**Tomorrow** (adding this because it keeps me organized and motivated)
- See whether I can SSH into the EC2 when my client's SSH service is turned off
- Spin up an EC2 in a VPC, SSH into it, and load a webpage on port 80
- Import an EC2 into a VPC CloudFormation template, deploy it, and test it works as expected (SSH & HTTP). Yay modular CloudFormation templates!

### [Day 1](#day-1)
#### April 15th, 2019
**Today's Progress**: 
- Set up my github pages to redirect to my personal site. Followed [Steve's blog post](https://dev.to/steveblue/setup-a-redirect-on-github-pages-1ok7) (thanks Steve!)
- [Version controlled terrycreamer.codes](https://github.com/trycrmr/terrycreamer.codes)
- Prepped my vscode to facilitate writing AWS CloudFormation templates. Followed [Matt's blog post](https://hodgkins.io/up-your-cloudformation-game-with-vscode) (thanks Matt!)

**Thoughts:** Simple day but feeling accomplished! Excited to dive into CloudFormation! 

**Link to work:** 
- [Personal Site](http://terrycreamer.com) with a working redirect from [trycrmr.github.io](https://trycrmr.github.io)!  ([Repo](https://github.com/trycrmr/terrycreamer.codes))
- [My Cloudformation repo](https://github.com/trycrmr/cloudformation)
