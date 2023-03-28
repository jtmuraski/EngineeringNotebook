ELB = Elastic Load Balancer
ASG = Auto Scaling Group

#### PDF Insert and Slides

![[Autoscaling and EBS Slides.pdf]]

### Load Balancing
- Load balancing are servers that forward traffic to multiple servers downstream
- This spreads the traffic load from multiple users to multiple backends, without the user even knowing or seeing a performance drop
- If an instance fails, it will redirect traffic away from the unhealthy instance
- ELB's are completly managed by AWS, so it is much cheaper than building and maintaining one yourself
- Integrates with many AWS services
- 
###### Health Checks
- Crucial for load balancers
- They enable the load balancer to know if an instance it forwards traffic to is available
- The ELB pings the instance through a port and router, and if an OK reply is not recieved, it marks that instance as unhealthy
###### Types of Load Balancers
- Classic (v1) - deprecated and no longer in use
- Application / ALB (v2) - 2016, HTTP, HTTPS, WebSocket
- __Network__  / NLB(v2) - 2017, TLP, TLS (Secure TLP), UDP
- __Gateway / GWLB__ - 2020, Operates at Layer 3 (Network layer) IP Protocol

###### Security
- ELB's are assigned to a security group. The security group allows all traffic in and out on specified ports. 
- The connected EC2 instances are then configured to only allow traffic to come in from the ELB
- The securtity group of the EC2 is linked to the Security group of the ELB

### Application Load Balancer
- Load balancer is in Layer 7 (HTTP)
- Load Balances to:
	- multiple applications across machines
	- multiple applications to the same machine (such as containers)
	- Support for HTTP/2 and WebSocket
	- Support redirects (from HTTP to HTTPS)
- Routing table can be set to different groups
	- Based on path in URL
	- Bassed on hostname in URL
	- Based on Query String, headers
- Great for microservices & container based application (Docker/Amazon ECS)
- Has a port mapping feature to redirect to a dynamic port in ECS
- Target Groups:
	- EC2 insances
	- ECS tasks 
	- Lambda functions
	- IP Addresses
- Can route to multiple different target groups
- Good To Knows:
	- Fixed hostname (XXX.region.elb.amazonaws.com)
	- The application servers (EC2) don't see the IP of the client directly
		- The true IP of the client is inserted in the header X-Forwarded-For
		- We can also get tPort (X-Forwarded-Port) and proto (X-Forwarded-Proto)
### Network Load Balancer
- Layer 4 balancer (TCP and UDP traffic)
- Can handle millions of request per second
- Less latency ~100 ms
- NLB has one static IP per AZ and supports assigning Elastic IP (which is helpful for whitelisting specific IP)
- Not free tier eligible
### Gateway Load Blanacer
- Deploy, scale and manage  afleet of 3rd party network virtual applicances in AWS
- Example: Firewalls, intrusive detection, and prevetion systems, Deep Packet Inspection Systems, payload manupulators
- 