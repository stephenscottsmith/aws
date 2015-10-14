# Amazon Web Services (AWS) Tutorial Notes

## Chapter 1: Cloud Concepts
* 3 types of Cloud Services:
 1. Infrastructure as a Service (IaaS)
   * Windows Azure, Rackspace Cloud
 2. Platform as a Service (PaaS)
   * Google App Engine, Heroku
 3. Software as a Service (SaaS)
   * Google Apps, Basecamp, Mint
* AWS does all 3
* Business Benefits
 * Minimal upfront infrastructure investment
 * Just-in-time infrastructure
 * Maximize efficiency of resources
 * Only pay for what you use
* Technical Benefits
 * Automation (scriptable API's) - helps focus on less menial tasks
 * Auto-scaling
 * Proactive scaling for anticipation of demand
 * Efficient development and improved testability - production environments can easily be cloned and tested
 * Disaster recovery - can deploy in various geographical locations
* Scalable architectures
 * Scaling Out (horizontal scaling) - adding capacity to a system by giving it more components or nodes
  * Example: adding more webservers to the systems to handle traffic
 * Scaling In (also horizontal scaling) - removing capacity from a system
  * Reducing the number of webservers
 * Scaling Up (vertical scaling) - adding resources to a single component or node in a system to handle a greater load
  * Example: increasing the number of CPUs or memory of a server
 * Scaling Down (also vertical scaling) - reducing the resources of a single component
 * ANY APPLICATION SHOULD BE DESIGNED TO TAKE ADVANTAGE OF ITS SCALABILITY
* Elasticity - the power to scale computing resources up and down easily 
* Constraints - no longer an issue because the cloud is made up of building blocks that allow you to scale quickly
* Role of the Admin - need to be aware of the flexibility and on-demand model provided by the cloud

## Chapter 2: Cloud Best Practices
* Design your system for failure
 * Minimize dependencies of components
 * Avoid single points of failure (i.e. a single database server without a backup)
* Implementing Elasticity - ability to scale cloud resources
 * Schedule-based proactive scaling
 * Event-based proactive scaling
 * Metric-based automatic scaling
 * Automate deployment process
 * Streamline the build-and-configuration process
 * Bootstrapping startup processes
* Decouple Components
  * Design principle that involves minimizing the dependencies between components
    * If a component fails, others continue to work
    * Example: using a load balancer to distribute demand a web server has of an app server
* Security
 * Customer of a cloud service like AWS is still responsible for a lot of the security 
 * AWS and other services like it take care of: physical security of servers, infrastructure, equipment, keeping customers separate
 * Customer is responsible for network and application security
 * Keep in mind:
    * Protect data transfer using SSL certificates
    * Protect the storage of data via encryption
    * Protect your AWS credentials:
      * All API requests should be sent over HTTPS
      * Rather than having your AWS secret access key be part of your app code, instead have it be passed in as an argument during the launch of the app and encrypted before sending it
      * Rotate your access keys often
      * Manage user access control using IAM

## Chapter 3: Designing For Failure
* EC2 is the service that provides users with virtual servers and elastic IP's
* Virtual Servers and Elastic IP's
  * Elastic IP allows you to map any IP address you own to any instance you own
    * Example: DNS -> IP -> Failed Server can be remapped DNS -> IP -> Working Server
* Regions and Availability Zones
  * EC2 instances can be launched in 1 or more geographical regions
  * Availability Zones - distinct locations designed to be isolated
* Amazon Machine Image (AMI)
  * AMI - is a basic unit of deployment and is a packaged environment and settings
  * Could have ones that correspond to Web Servers, App Servers, etc.
  * Made up of:
    * Template for root volume
    * Launch Permissions
    * Block device mapping
* Elastic Load Balancing
  * Balances traffic across EC2 instances and AZ's
  * Achieves greater fault tolerance
  * Scales request-handling capability automatically
  * Supports HTTP, HTTPS, and TCP
  * Set up and configure health checks
  * Scales dynamically
  * Single CNAME for DNS configuration
  * Use ELB to easily distribute your system across multiple zones to make sure it stays up and running
* Resource and Application Monitoring (Cloudwatch)
  * Monitor resources immediately and automatically 
* Elastic Block Storage (EBS)
  * Design to retain data
  * Elastic Block Storage (Persistent)
  * Ephemeral Storage (Not Persistant)
  * Created separately from instances, you attach them to one another
  * 2 Types of EBS: Standard Volumes, Provisioned IOPS Volumes
  * Attach multiple volumes to a single instance
  * Specify I/O performance
  * Format with a filesystem, use like any other block device
  * Create point-in-time snapshots that can be used to instantiate new volumes
  * Copy snapshots across regions
  * Use Cloudwatch to view performance metrics
* Relational Database Service (RDS)
  * In case of failure, ensure a safe and quick recovering
  * Set up, operate, and scale a relational database
  * Easy to manage
  * Easily achieve high availability and redundancy
  * Create a database instance
  * Specify Engine (MySQL, Postgres, etc.)
  * Specify instance size
  * Connect once created
  * Monitor with Cloudwatch
  * No SSH access
  * No root access
  * Amazon manages patches, backups, failover, etc.
  * Consider using RDS to simplify database security, administration, backups, redundancy, failovers, scalability, and geographical distribution

## Chapter 4: Implementing Elasticity: Automating Infrastructure
* Bootstrapping
  * Creating a self-sustaining startup process
  * Process needed to get your app running on EC2
  * Tell instances who they are and what their role is
  * Provide needed resources
  * Example Process:
    * Mount needed drives
    * Start needed services
    * Update files or scripts
    * Update software 
    * Register with load balancer
  * Tools
    * Run custom scripts and tools
    * Chef or Puppet
    * Opsworks (Free application management service)
    * Access to instance metadata
    * Cloud-Init (Linux)
    * EC2Config (Windows)
    * Write the scripts and configuration necessary to bootstrap your instances
* Autoscaling Groups
  * You define your scale-out and scale-in parameters
  * The service will scale accordingly
  * Components:
    * Launch Configuration: What to scale
    * Auto-Scaling Group: Where to launch
    * Scaling Policy: How to launch
      * This is where YOU can define metrics to handle scaling
  * Take advantage of the Auto-Scaling service to greatly simplify the process of automating your scaling.
* Scalable Storage *Simple Storage Service and CloudFront)
  * Simple Storage Service (S3)
  * Glacier
  * CloudFront
  * Storage Options AWS Provides:
    * Block Storage - EBS/Instance Storage
    * Object Storage - S3, Glacier, CloudFront
    * Storage Gateway (Sync Volumes) - Connect local environment with AWS infrastructure
    * Relational Databases - RDS
    * NoSQL Databases - DynamoDB
    * In-Memory Cache - Elasticahe
    * Content Caching
  * S3
    * Object Store
    * Objects stored in 'buckets'
    * Object retrieved by 'keys'
    * Not a traditional filesystem
    * Minimal metadata management
    * No search
    * Built to be incredibly durable
    * High Availability
    * RRS - Reduced Redundancy Storage (less costly)
    * Unlimited Storage Capacity
    * 5TB limit per object
    * REST/SOAP API protocol access
    * Eventual Consistency Model
  * Glacier
    * For archival data
    * 3-5 hour retrieval time
    * Highly durable
    * Cost-effective
    * Manage objects through S3
  * CloudFront
    * Define and configure origin server
    * Create a new CloudFront distribution
    * Use the configurated domain name in your application
    * Pay only for what you use
  * Take advantage of the object storage options to improve the scalability, availability, durability, and performance of storing and accessing your application assets
* Elastic Beanstalk
  * Paas (Platform as a Service)
    * Capacity Planning
    * Load Balancing
    * Auto-Scaling
    * Health Monitoring 
  * Supports Java, .NET, PHP, Python, Node.js, Ruby
  * Sends application and server logs to S3
  * You retain control over the resources
  * Example Workflow
    * Create your application
    * Create Elastic Beanstalk environment
    * Install Git version control
    * Commit and publish to Beanstalk via Git
    * Access app at a custom URL
  * Environment
    * Single micro EC2 instance
    * Built from Amazon Linux or Windows 2008 Server
    * Runs an ELB to distribute traffic 
    * Configures EC2 for Auto-Scaling
    * Provides a URL
    * You can configure High Availability
    * No additional charge for Beanstalk
  * Consider taking advantage of Elastic Beanstalk to deploy your applications in a fully managed container in the cloud.
* CloudFormation and CloudFormer
  * Provides an easy way to manage related resources
  * Define an app stack as text template files
  * Use version control to manage environment
  * Quickly Rebuild the Stack
    * Deploy to Development or QA
    * Move Regions
    * Share a stack with someone else
    * Deploy via Application Management Console or the API
  * JSON Notation
  * CloudFormer
    * Configure and launch required resources
    * Create and launch a CloudFormer stack
    * Use CloudFormer to create a template
    * Shut down the CloudFormer stack
    * Use the CloudFormation template as needed
  * Use CloudFormation templates to manage and version-control your entire AWS application stack, and easily replicate your stack to new environments.

## Chapter 5: Decoupling Your Components
* Simple Queue Service (SQS)
  * Decoupling Components
    * Reduce tight dependencies
    * Scale bigger and better
    * If a component becomes unresponsive, others continue on
  * SQL 
    * Message queueing software in the cloud
    * Reliable, highly scalable, distributed
    * Pass messages between computers and app components
    * Allows communication with independence
  * Tightly Coupled System vs Loosely Coupled System
    * Have controllers within the system implemented with queues for each of the controllers
  * Watermarking App Example
    * User uploads an image
    * Image is downsized
    * A watermark is added
    * User is notified
  * **Decoupling Components Lesson #1:** Use SQS to facilitate the communication between your independent components to bind them together into a fail-safe, scalable, and performant application
* Simple Workflow Service (SWF)
  * Helps define, manage and coordinate tasks for a given workflow
  * Deliver boilerplate code
  * Ecommererce Common Workflow
    * Customer places order - validate order -> payment is successful -> ship order -> record completion -> end
                              order verifiers-> CC verifiers -> warehouse employees -> database records
  * SWF handles workflow management
  * Deciders  
    * You configure decisions with Deciders
    * Responds to results and determines what to do next
    * Decisions are event-driven
  * Activity Worker
    * Performs the work assigned by SWF tasks
    * Work is scheduled by the Decider
    * Can run from anywhere
  * **Decoupling Components Lesson #2:** Consider using SWF to help with more complex workflows and keep your components independent from one another. 
* Simple Notification Service (SNS)
  * Notify people or applications from the cloud
  * Create topics
  * Publish subscribe protocol
  * Example: Notify Operations team of an issue in production
    * Monitor systems using CloudWatch
    * Raise an alarm based on an event
    * Alarm High CPU -> Topic-DevOps Alerts -> E-Mail and SMS
  * Sends to all subscribers using the protocol defined
  * Can configure different messages based on protocol so e-mail can be different from SMS
  * JSON structure used when sending different messages for the same alert
  * Push Rather Than Pull
    * Posting to a topic causes a message to send immediately
    * SNS lets us set up a push notification systems
    * SQS requires applications to poll constantly (Pull approach)
    * SNS keeps applications independent and decoupled
  * **Decoupling Components Rule #3:** When applicable, use SNS to help with communication between different components, as well as for having those components work in parallel for efficient and scalable systems.
* Scalable NoSQL Data Store (DynamoDB) 
  * NoSQL, No-Relational, Schemaless
  * Low latency
  * High performance, High throughput
  * Data stored on SSD
  * Automatically replicated across multiple AZ's
  * Helps keep your application stateless
  * Example: User session management
  * **Decoupling Components Rule #4:** Make your applications as stateless as possible, and when a session state is needed, store this state outside of your application using DynamoDB

## Chapter 6: Keeping Things Secure
