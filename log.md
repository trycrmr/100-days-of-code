# Terry's 100 Days Of Code - Log

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
