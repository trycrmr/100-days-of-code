# Terry's 100 Days Of Code - Log

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
