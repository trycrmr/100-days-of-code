# Terry's 100 Days Of Code - Log

### [Day 13](#day-13)
#### April 27th and 28th, 2019
**Today's Progress**:
- Did another 20 practice questions for the AWS Certified DevOps Engineer - Professional exam

**Thoughts:** Life had me on the move for the whole day yesterday. It was my first missed day so far. I got lots done, just not 100 days of code things. Hopefully it won't happen again! I'm ensuring I actually do 100 days by counting this as day 13, but accounting for the April 27th and 28th. 

Today I did another twenty practice questions. I'm definitely learning because I get more opinionated about the answers to the questions. At times, it can feel like something I've learned from previous questions contradicts what I learn from newer questions. Most of the time the explanation spells out the difference, but occasionally it doesn't. This can be frustrating, but I had this experience before prepping for the AWS Solutions Architect Professional exam. 

There have been several cases around handling log files for analysis given business requirements from several parties. This is a really neat and practical system, incorporating streaming aspects with analytics. It feels like a pretty common experience across architectures, and it's getting me excited to practice building such a ubiquitious OLTP to OLAP setup. The patterns here can be replicated across any sort of streaming data into an analytical, persistent data store. Questions like these have me longing for a time when I switch back to pragmatic drilling with AWS services. Actually getting the certification is pulling at my like a strong magnet, so I'll probably follow through, but, oh boy, it'll be a blast standing up the architectures I'm being asked about! 

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
