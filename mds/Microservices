To Do:
HTTP Resource API
JSON

Definition:
The term "Microservice Architecture" describe a particular way of designing software applications as suites of independently deployable services. While there is no precise definition of this architectural style, there are certain common characteristics around organization around business capability, automated deployment, intelligence in the endpoints, and decentralized control of languages and data.

Microservice Architectural Style – is an approach to developing a single application as a suite of small services each running in its own process and communicating with lightweight mechanisms (often HTTP resource API)

Talking points:
•	Particular way of designing application
•	Around business capability (Rather than infrastructure/technology – UI, Server, and DBA)
•	Independently deployable
•	Automated deployable
•	Running in its’s own process
•	Communicating with lightweight protocol (often HTTP resource API)
•	Decentralized control of languages and data
•	Issues with monolith application
•	Small change requires entire monolith to be rebuilt and deployed
•	Hard to keep up with modular structure over time
•	Scaling requires entire application scaling
•	Spring Boot: build Java-based, REST oriented microservices quickly; then package and deploy it without need for external application container
•	Spring Cloud: wraps popular cloud management microservice frameworks

Characteristics:
Componentization via Services
	Component is unit of software that is independently replaceable and upgradable.
Libraries vs. Services
A service may consist of multiple processes that will always be developed and deployed together, such as an application process and a database that's only used by that service.
Organized around Business Capabilities
Orders, Shipping, Recommendations
Two Pizza team size
Direct communication with Customer and End Users
Products not Projects
Smart endpoints and dumb pipes
	Not smart infrastructure like ESB
Communication via REST or MQ
Decentralized Governance
Decentralized Data Management
	One database per Service
	Data sharing through Service that wraps data
Infrastructure Automation
	Continuous Delivery
Blue/Green deployment
Design for failure
Evolutionary Design

Patterns:
Core Microservice Development Patterns
	Service Granularity: too coarse-grained => overlap into different business problems -> difficult to maintain; too fine-grained -> increases complexity; turn app into “dumb” data abstraction layer
	Communication Protocols: JSON
	Interface Desgin
	Configuration Management
	Event Processing
Microservice Routing Patterns
	Service Routing: single logic URL; acts as policy enforcement point like authorization, authentication and content checking
	Service Discovery: abstracts physical location
Microservice Client Resiliency Patterns
	Client-side load balancing: 
	Circuit Breakers Pattern (not repeatedly call back; instead fail-fast)
	Fallback Pattern
	Bulkhead Pattern (one misbehaving service does not take up all resources)
Microservice Build/Deployment Patterns
	Build and Deployment Pipeline
	Infrastructure as Code
	Immutable Servers
	Phoenix Servers

 
