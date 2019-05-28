# Terry's 100 Days Of Code - Log

### [Day 36](#day-36)
#### May 28th, 2019
**Today's Progress**:
- Attempted to write my own tooling for outputting the current application state and what action caused the current application state to change
- Start incorporating AWS Amplify UI components using React Router to configure the proper redirects

**Thoughts:** Wrote a little bit of middleware and began getting auth UI components put together! With the use-global-hook npm module I wanted to have the current state of the application outputted to the console. Ideally, anytime an action was called, the before and after state would get printed. I was able to get the current state to print everytime the useGlobal hook was called, but I had more trouble getting the action to print. I wanted to iterate over the actions object and (...maybe this is the right word...) decorate each action with a function that would print the action and the before/after application state objects. After about an hour of trying a few things, I had to move on to actually progressing getting the authentication flow to work instead of investing too much time into tooling. Every so often I realize I "don't know JavaScript" and I probably could do with a review of Kyle Simpson's books or some coding challenges to continue leveling up my JavaScript skills.

Did lots of laying the groundwork of different components that would act as the authentication flow throughout the application (sign in, sign out, sign up, etc.). Tomorrow I should get to actually hitting the endpoints to interact with the Cognito User Pools via the Amplify API. Once that's done I'll get to submitting my "vote" to the backend; That's when we're cooking with fire and can get to the SQS, DynamoDB, etc. backend architecture work! 

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
