# Microservices & Service Discovery

---

_The microservices architectural style is an approach to developing a single application as a suite of small services, each running it's own process and communicating with lightweight mechanisms_
- Martin Fowler

---

# Monolithic app vs Microservices

---

# Enterprise application

- Often built using three parts
 - User interface
 - Database
 - Server-side application

- The server-side app will handle user requests, execute logic, retrieve and update data and show it to the user

The server-side app is what we call a **monolith**

---

# Monolithic != bad

A lot of successful applications have been and are still written as monoliths

But some apps are in need of faster change cycles, and that's usually were it breaks down

A small change made to a part of the application usually requires the entire monolith to be rebuilt and redeployed

Scaling the app requires running multiple copies of the entire application, which might not be the best idea or even possible

---

# Let's look at an example

---

# Monolithic application

![right, fit](http://www.slashroot.in/sites/default/files/Monolithic%20Application%20Architecture.png)

---

# Scaling a monolithic application

![right,fit](http://www.javacodegeeks.com/wp-content/uploads/2016/04/Monolithic-2.jpg)

---

# Move to a microservices architecture

![right,fit](http://blog.philipphauer.de/wp-content/uploads/2015/04/Monolith-vs-Microservices.png)

---

# It's not just about scale, but also separation of concern

---

# Traditional organisation layout

![fit,right](http://martinfowler.com/articles/microservices/images/conways-law.png)

---

# Business capability organization layout

![fit,right](http://martinfowler.com/articles/microservices/images/PreferFunctionalStaffOrganization.png)

---

# This also leads to new stacks

 - Developers can use the right tool for the job and are not necessarily locked into one tool or language
 - New processes are explored and applied
 - Innovation can happen quicker
 - New deployments can be done daily or weekly instead of taking months

---

# So how do we keep track of all the microservices?

---

# Service Discovery!

---

![fit](https://assets.digitalocean.com/articles/docker_ecosystem/Discover-Flow.png)

---

# What are some Service Discovery tools?

 - etcd, by CoreOS
 - Consul, by Hashicorp
 - Zookeeper, by Apache
 - SkyDNS (built on top of etcd)
 - Eureka, by Netflix
 - Smartstack, by AirBnB
 - All of them open source!

---

# Learn more

 - [DigitalOcean tutorial](https://www.digitalocean.com/community/tutorials/the-docker-ecosystem-an-introduction-to-common-components)
 - [Microservices by Martin Fowler](http://martinfowler.com/articles/microservices.html)
 - [Scaling your app with message oriented decoupled architecture by Cantina](http://cantina.co/scaling-your-app-with-message-oriented-decoupled-architecture/)

---

# ClOUD NATIVE APPLICATION
## Structure vs Unstructured Platforms

---
# What Makes Cloud Native Apps Different?
 - Operate At Much Greater Scale On Much More Data - Tend To Be Built On Microservices - Use New Development Methods - As Well As New Deployment, Organizational and Management Models - With Open Source Components At All Levels

---
# Cloud Native Apps Infrastructure Needs
 - Programmability (“Infrastructure As Code”) - Elasticity (Which Demands A Scale-Out Architecture) - Economics (Steers Towards Commodity + Software-based) - Strong Instrumentation And Telemetry Of Infrastructure Layer

---
# Two Types Of Cloud Native Platforms
## Unstructured and Structured
---

# Unstructured
 - Ultra-flexible - Max Opportunity For Optimization - For Companies Where Platform = Core Competency - Common In SaaS Startups Where There Are Relatively Few, Bespoke Apps


---
# Unstructured Con't

![fit, right](http://wikibon.com/wp-content/uploads/ContainerArch31.png)

---
# Structured
 - Opinionated - Fastest & Reliable Outcome - Largest Community Of Talent - Common In Enterprise Where There Are Many Apps

---
# Structured Con't
![fit, right](http://wikibon.com/wp-content/uploads/PaaS-Platforms.png)

---
# What Solutions are out there?

![fit, right](http://wikibon.com/wp-content/uploads/Structured-Unstructured-Spectrum.png) 

---

# Overall Look
![fit, right](http://wikibon.com/wp-content/uploads/Structured-Unstructured.png)

---

# Summary/Aligning The Organisation and The Platform
 - The first key element is how is IT organisation or business is organised
 - The second key element is the technical skills within the IT organisation or business
 - The third key element is the existing applications within a customer’s portfolio
 - The fourth key element is the granularity of policy management
 - The fifth key element is the customer’s willingness to work with open source projects and communities

---


# Data Persistance

---

# Object Storage
# NoSQL "Not Only"
# Block/File
# HDFS
# In-Memory
# RDBMS


---

# Where are we at?

---

* RDBMS Can Do Everything, Right?
  * Transactions, performance...
* Not Quite

---

RDBMs Are Good At:

* SQL (common interface)
* Industry Support
* Small Scale

---

RDBMs Are Bad At:
* Simpler Notation
* Ultra Low Latency
* Large Scale (>10 nodes)
* Changes (schema, etc) on the fly


---

#Lets Use the Right Tool for the Right Job

---

NoSQL Are Good At:

* Simple Notation / Access
* Low Latency
* Large Scale
* Changes
  * With great power comes great responsibility
  
![inline](http://cdn.fansided.com/wp-content/blogs.dir/315/files/2014/11/unclebendad.jpg)

---

NoSQL (Might Be) Bad At:

* Transactional Consistency
* SQL (JOINs, etc)
* Off the Shelf Application Support

---

# Examples of SQL:

* Oracle
* MySQL
* Postgres
* MSSQL Server


---

# CAP Theorem

![inline](http://i.imgur.com/JNN7Ucs.png)

---

#4 Common Types

---

#Key Value

* Stores a simple value (10,456,345) in a 'key': ("usercount")
* Simple 'CRUD' semantics
  * Create, Read, Update, Delete
* No schema at all, generally
* Stunningly Scalable (hundreds->thousands of nodes)
* "Get me the current MacOS user count"
* DSSD/Fusion IO

---

* Examples:
  * Redis (http://try.redis.io/)
  * Memcached
  * Aerospike
  * Cassandra
  * Basho Riak
  * LevelDB
  * Couchbase

---

# Document Stores

* Store Larger Scale Documents
  * Usually in standard encoding: `JSON`, `YML`, `BSON`
  * *not* Word documents

---

```javascript
{
    "id": 1,
    "name": "A green door",
    "price": 12.50,
    "tags": ["home", "green"]
}

```

---
  
* Retrieve Documents Based on Key *or* Contents
* Highly Scalable (tens to hundreds of nodes)
* "Show me documents that talk about MacOS"
* ScaleIO

---

* Examples:
  * CouchDB / Cloudant (try it for free: https://cloudant.com/sign-up/)
  * MarkLogic (popular in .gov)
  * MongoDB (try it for free: https://mongolab.com/)
  * Amazon SimpleDB (outdated)
  * BaseX

---

# Graph Database

* Represents connections between objects (nodes):
* For instance, if "Wikipedia" were one of the nodes, one might have it tied to properties such as "website", "reference material", or "word that starts with the letter 'w'"
* For associating simple data types, these tend to be orders of magnitude faster than SQL
* "Show me everyone that likes MacOS"
* Rough Scene :)

^ Twitter finding friends
^ Logistics shortest route

---


![inline](http://i.imgur.com/4xzfVMi.png)

* Examples:
  * Neo4j (http://console.neo4j.org/)
  * InfiniteGraph
  * AllegroGraph
  * BlazeGraph (used in ViPR SRM)

---

# (Wide) Column Store

* Uses tables, rows, columns, but does not fix schema like SQL (because its focused on storing the columns, not the rows)
* Great for computing aggregates of huge amounts of data (common in Big Data, data warehouse)
* "Show me everyone that clicked this link between yesterday and today, sorted by age"
  * Where total clicks is tens of millions
* Isilon, ScaleIO, VXRack, NHC, DCA

---

* Examples:
  * HBase (Hadoop)
  * Greenplum
  * Vertica
  * Teradata
  * Amazon Redshift (https://aws.amazon.com/redshift/)
  * Google BigQuery


---

# What Is Object Storage?

###Traditional Concepts:

* Block
* File (possibly on top of block)
* Tape

---

## Block

* Accessed via logical block address
* Random access anywhere in the device
* Low latency - transaction focused
* 512 / 4K block sizes
* Difficult to share across systems
* Difficult to replicate efficiently

![fit,right](images/block.png)


---

## File

* Accessed via filename
* Random access anywhere in the file
* Moderate latency
* File sizes 2GB-~2PB
* Difficult to share across systems (NFS doesn't count)
* Still focused on transactions

---

## Tape 

* Accessed by 'ID' on tape.
* Linear access only
* Very high latency (think minutes)
* Tough to share
* Focused on $/GB

---

# A 4th Idea - Object Storage 

Something that has:

* low $/GB (not quite as low as tape)
* Easy to share across thousands of systems
* Easy to replicate - eventually consistent
* Accessed by HTTP (modern)
* Objects (of any reasonable size) are the unit of access, not blocks or segments
* Rich metadata
* Response time in hundreds of milliseconds to seconds

---

![fit](images/object.png)

---

# EMC's Story

* FilePool -> EMC Centerra
* Atmos
* Isilon
* ECS Object

---

# Other Common Implementations

* Amazon S3
* Rackspace Files
* Google Cloud Storage
* Scality
* Ceph

---

# Where Is It Used?

* Cloud scale storage of:
  * Images & Videos
  * Audio
  * Documents
  * Large Datasets

---

#Benefits

* Techniques like SATA drives and erasure coding make it VERY efficient in $/GB ($0.02/GB)
* Native HTTP management and access make it very easy to develop for and access with any language / framework
* Lack of hard consistency makes it easy to replicate across long distances.

---

# In Combination:

Along with cloud native platforms like Cloud Foundry, object storage is commonly used with:

* A modern language like Python or Node.JS
* A NoSQL database for managing user metadata
* A object store for managing large scale user data (uploaded images, music, etc)

---

#Keywords

If your business is thinking about:

* Cloud Native applications
* Large scale image repositories (including healthcare)
* Hadoop data
* Archive storage

talk to your local object storage vendor

---

#Conclusions

* Lots of different options
  * Let your data dictate management method
* SQL is not always the right choice
* Object is a Great new option for CNA 
	* Try https://portal.ecstestdrive.com/

