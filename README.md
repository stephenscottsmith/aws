# Amazon Web Services (AWS) Tutorial Notes

## Chapter 1: Cloud Concepts

### Cloud Services
* There are 3 types of Services:
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

