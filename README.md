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
