# Software Architecture Interview Questions

## Q1: Why Do You Need Clustering? ⭐⭐

**Answer:**
_Clustering_ is needed for achieving high availability for a server software. The main purpose of clustering is to achieve 100% availability or a zero down time in service. A typical server software can be running on one computer machine and it can serve as long as there is no hardware failure or some other failure. By creating a cluster of more than one machine, we can reduce the chances of our service going un-available in case one of the machine fails.

Doing clustering does not always guarantee that service will be 100% available since there can still be a chance that all the machine in a cluster fail at the same time. However it in not very likely in case you have many machines and they are located at different location or supported by their own resources.

**Source:** _fromdev.com_

## Q2: What Is A Cluster? ⭐⭐

**Answer:**
A cluster is group of computer machines that can individually run a software. Clusters are typically utilized to achieve high availability for a server software. Clustering is used in many types of servers for high availability.

- **App Server Cluster**
  An app server cluster is group of machines that can run a application server that can be reliably utilized with a minimum of down-time.
- **Database Server Cluster**
  An database server cluster is group of machines that can run a database server that can be reliably utilized with a minimum of down-time.

**Source:** _fromdev.com_

## Q3: What Is Scalability? ⭐⭐

**Answer:**
Scalability is the ability of a system, network, or process to handle a growing amount of load by adding more resources. The adding of resource can be done in two ways

- **Scaling Up**
  This involves adding more resources to the existing nodes. For example, adding more RAM, Storage or processing power.
- **Scaling Out**
  This involves adding more nodes to support more users.

Any of the approaches can be used for scaling up/out a application, however the cost of adding resources (per user) may change as the volume increases. If we add resources to the system It should increase the ability of application to take more load in a proportional manner of added resources.

An ideal application should be able to serve high level of load in less resources. However, in practical, linearly scalable system may be the best option achievable. Poorly designed applications may have really high cost on scaling up/out since it will require more resources/user as the load increases.

**Source:** _fromdev.com_

## Q4: What Is Session Replication? ⭐⭐⭐

_Session replication_ is used in application server clusters to achieve session failover. A user session is replicated to other machines of a cluster, every time the session data changes. If a machine fails, the load balancer can simply send incoming requests to another server in the cluster. The user can be sent to any server in the cluster since all machines in a cluster have copy of the session.

Session replication may allow your application to have session failover but it may require you to have extra cost in terms of memory and network bandwidth.

## Q5: What Is Load Balancing? ⭐⭐⭐

_Load balancing_ is the process of distributing network traffic across multiple servers.

This ensures no single server bears too much demand. By spreading the work evenly, load balancing improves application responsiveness.
It also increases availability of applications and websites for users.
Modern applications cannot run without load balancers.
Over time, software load balancers have added additional capabilities including security and application.

There is a variety of load balancing methods, which use different algorithms for different needs.

- _Least Connection Method_: This method directs traffic to the server with the fewest active connections. This approach is quite useful when there are a large number of persistent client connections which are unevenly distributed between the servers.
- _Least Response Time Method_: This algorithm directs traffic to the server with the fewest active connections and the lowest average response time.
- _Least Bandwidth Method_: This method selects the server that is currently serving the least amount of traffic measured in megabits per second (Mbps).
- _Round Robin Method_: This method cycles through a list of servers and sends each new request to the next server. When it reaches the end of the list, it starts over at the beginning. It is most useful when the servers are of equal specification and there are not many persistent connections.
- _Weighted Round Robin Method_: The weighted round-robin scheduling is designed to better handle servers with different processing capacities. Each server is assigned a weight (an integer value that indicates the processing capacity). Servers with higher weights receive new connections before those with less weights and servers with higher weights get more connections than those with less weights.
- _IP Hash_: Under this method, a hash of the IP address of the client is calculated to redirect the request to a server.

## Q6: What Is Sticky Session Load Balancing? What Do You Mean By "Session Affinity"? ⭐⭐⭐

_Sticky session_ or a _session affinity technique_ is another popular load balancing technique that requires a user session to be always served by an allocated machine.

In a load balanced server application where user information is stored in session it will be required to keep the session data available to all machines. This can be avoided by always serving a particular user session request from one machine. The machine is associated with a session as soon as the session is created. All the requests in a particular session are always redirected to the associated machine. This ensures the user data is only at one machine and load is also shared.

This is typically done by using `SessionId` cookie. The cookie is sent to the client for the first request and every subsequent request by client must be containing that same cookie to identify the session.

### What Are The Issues With Sticky Session?

There are few issues that you may face with this approach:

- The client browser may not support cookies, and your load balancer will not be able to identify if a request belongs to a session. This may cause strange behavior for the users who use no cookie based browsers.
- In case one of the machine fails or goes down, the user information (served by that machine) will be lost and there will be no way to recover user session.

## Q7: What Is Fail Over? ⭐⭐⭐

Fail over means switching to another machine when one of the machine fails. Fail over is a important technique in achieving high availability. Typically a load balancer is configured to fail over to another machine when the main machine fails.

To achieve least down time, most load balancer support a feature of heart beat check. This ensures that target machine is responding. As soon as a hear beat signal fails, load balancer stops sending request to that machine and redirects to other machines or cluster.

## Q8: What Do You Mean By High Availability? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q9: "People who like this also like... ". How would you implement this feature in an e-commerce shop? ⭐⭐⭐

> This is an open-ended question. Provide some personal experience as an answer.

## Q10: What Is ACID Property Of A System? ⭐⭐⭐

**ACID** is a acronym which is commonly used to define the properties of a relational database system, it stand for following terms:

- **Atomicity** : This property guarantees that if one part of the transaction fails, the entire transaction will fail, and the database state will be left unchanged.
- **Consistency** : This property ensures that any transaction will bring the database from one valid state to another.
- **Isolation** : This property ensures that the concurrent execution of transactions results in a system state that would be obtained if transactions were executed serially.
- **Durable** : means that once a transaction has been committed, it will remain so, even in the event of power loss.

## Q11: What Is Middle Tier Clustering? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q12: How Do You Update A Live Heavy Traffic Site With Minimum Or Zero Down Time? ⭐⭐⭐

Deploying a newer version of a live website can be a challenging task specially when a website has high traffic. Any downtime is going to affect the users.

There are a few best practices that we can follow:

### Before deploying on Production:

- Thoroughly test the new changes and ensure it working in a test environment which is almost identical to production system.
- If possible do automation of test cases as much as possible.
- Create a automated sanity testing script (also called as smoke test) that can be run on production (without affecting real data). These are typically readonly type of test cases. However depending on your application needs you can add more cases to this. Make sure it can be run quickly by keeping it short.
- Create scripts for all manual tasks(if possible), avoiding any hand typing mistakes during day of deployment.
- Test the script to make sure they work on a non-production environment.
- Keep the build artifacts ready. e.g application deployment files, database scripts, config files etc.
- Create a checklist of things to do on day of deployment.
- Rehearse. Deploy in a non-prod environment is almost identical to production. Try this with production data volumes (if possible). Make a note of time required for your tasks so you can plan accordingly.

### When doing deploying on a production environment:

- Use Green-Blue deployment technique to reduce down-time risk
- Keep backup of current site/data to be able to rollback
- Use sanity test cases before doing a lot of in depth testing

## Q13: Explain Blue-Green Deployment Technique ⭐⭐⭐

`Blue-green deployment` is a technique that reduces downtime and risk by running two identical production environments called `Blue` and `Green`. At any time, only one of the environments is live, with the live environment serving all production traffic. For this example, `Blue` is currently live and `Green` is idle.

As you prepare a new version of your software, deployment and the final stage of testing takes place in the environment that is not live: in this example, `Green`. Once you have deployed and fully tested the software in `Green`, you switch the router so all incoming requests now go to `Green` instead of `Blue`. `Green` is now live, and `Blue` is idle.

This technique can eliminate downtime due to application deployment. In addition, blue-green deployment reduces risk: if something unexpected happens with your new version on `Green`, you can immediately roll back to the last version by switching back to `Blue.`

## Q14: How can you keep one copy of your utility code and let multiple consumer components use and deploy it? ⭐⭐⭐

Once you start growing and have different components on different servers which consumes similar utilities, you should start managing the dependencies.

There is a tool for that, it's called `npm` or `nuget`. Start by wrapping 3rd party utility packages with your own code to make it easily replaceable in the future and publish your own code as private npm package. Now, all your code base can import that code and benefit free dependency management tool. It's possible to publish npm packages for your own private use without sharing it publicly using private modules, private registry or local npm packages.

## Q15: What does SOLID stand for? What are its principles? ⭐⭐⭐

**S.O.L.I.D** is an acronym for the first five object-oriented design (_OOD_) principles by Robert C. Martin.

- **S** - Single-responsiblity principle. A class should have one and only one reason to change, meaning that a class should have only one job.
- **O** - Open-closed principle. Objects or entities should be open for extension, but closed for modification.
- **L** - Liskov substitution principle. Let q(x) be a property provable about objects of x of type T. Then q(y) should be provable for objects y of type S where S is a subtype of T.
- **I** - Interface segregation principle. A client should never be forced to implement an interface that it doesn't use or clients shouldn't be forced to depend on methods they do not use.
- **D** - Dependency Inversion Principle. Entities must depend on abstractions not on concretions. It states that the high level module must not depend on the low level module, but they should depend on abstractions.

## Q16: Defend the monolithic architecture. ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q17: What Is Sharding? ⭐⭐⭐⭐

_Sharding_ is a architectural approach that distributes a single logical database system into a cluster of machines. Sharding is _Horizontal partitioning_ design scheme. In this database design rows of a database table are stored separately, instead of splitting into columns (like in _normalization_ and _vertical partitioning_). Each partition is called as a _shard_, which can be independently located on a separate database server or physical location.

Sharding makes a database system highly scalable. The total number of rows in each table in each database is reduced since the tables are divided and distributed into multiple servers. This reduces the index size, which generally means improved search performance. The most common approach for creating shards is by the use of consistent hashing of a unique id in application (e.g. user id).

### Partitioning Criteria

**a. `Key or Hash-based partitioning`**: Under this scheme, we apply a hash function to some key attributes of the entity we are storing; that yields the partition number. For example, if we have 100 DB servers and our ID is a numeric value that gets incremented by one each time a new record is inserted. In this example, the hash function could be ‘ID % 100’, which will give us the server number where we can store/read that record. This approach should ensure a uniform allocation of data among servers. The fundamental problem with this approach is that it effectively fixes the total number of DB servers, since adding new servers means changing the hash function which would require redistribution of data and downtime for the service. A workaround for this problem is to use `Consistent Hashing`.

**b. `List partitioning`**: In this scheme, each partition is assigned a list of values, so whenever we want to insert a new record, we will see which partition contains our key and then store it there. For example, we can decide all users living in Iceland, Norway, Sweden, Finland, or Denmark will be stored in a partition for the Nordic countries.

**c. `Round-robin partitioning`**: This is a very simple strategy that ensures uniform data distribution. With ‘n’ partitions, the ‘i’ tuple is assigned to partition (i mod n).

**d. `Composite partitioning`**: Under this scheme, we combine any of the above partitioning schemes to devise a new scheme. For example, first applying a list partitioning scheme and then a hash based partitioning. Consistent hashing could be considered a composite of hash and list partitioning where the hash reduces the key space to a size that can be listed.

### The downsides of sharding:

- It requires application to be aware of the data location.
- Any addition or deletion of nodes from system will require some rebalance to be done in the system.
- If you require lot of cross node join queries then your performance will be really bad. Therefore, knowing how the data will be used for querying becomes really important.
- A wrong sharding logic may result in worse performance. Therefore make sure you shard based on the application need.

## Q18: What Is IP Address Affinity Technique For Load Balancing? ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q19: What Is BASE Property Of A System? ⭐⭐⭐⭐

**BASE** properties are the common properties of recently evolved `NoSQL` databases. According to CAP theorem, a BASE system does not guarantee consistency. This is a contrived acronym that is mapped to following property of a system in terms of the CAP theorem:

- **Basically available** indicates that the system is guaranteed to be available
- **Soft state** indicates that the state of the system may change over time, even without input. This is mainly due to the eventually consistent model.
- **Eventual consistency** indicates that the system will become consistent over time, given that the system doesn't receive input during that time.

## Q20: Explain threads to your grandparents ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q21: Why layering your application is important? Provide some bad layering example. ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q22: Why should you structure your solution by components? ⭐⭐⭐⭐

For medium sized apps and above, monoliths are really bad - having one big software with many dependencies is just hard to reason about and often leads to spaghetti code. Even smart architects — those who are skilled enough to tame the beast and 'modularize' it — spend great mental effort on design, and each change requires carefully evaluating the impact on other dependent objects.

The ultimate solution is to develop small software: divide the whole stack into self-contained components that don't share files with others, each constitutes very few files (e.g. API, service, data access, test, etc.) so that it's very easy to reason about it.

Some may call this 'microservices' architecture — it's important to understand that microservices are not a spec which you must follow, but rather a set of principles.

- Structure your solution by self-contained components is good (orders, users...)
- Group your files by technical role is bad (ie. controllers, models, helpers...)

## Q23: Are you familiar with The Twelve-Factor App principles? ⭐⭐⭐⭐⭐

_Twelve-Factor App_ is a methodology for building software as a service applications. These best practices are designed to enable applications to be built with portability and resilience when deployed to the web.

1. _Codebase_ - There should be exactly one codebase for a deployed service with the codebase being used for many deployments.
2. _Dependencies_ - All dependencies should be declared, with no implicit reliance on system tools or libraries.
3. _Config_ - Configuration that varies between deployments should be stored in the environment.
4. _Backing services_ - All backing services are treated as attached resources and attached and detached by the execution environment.
5. _Build, release, run_ - The delivery pipeline should strictly consist of build, release, run.
6. _Processes_ - Applications should be deployed as one or more stateless processes with persisted data stored on a backing service.
7. _Port binding_ - Self-contained services should make themselves available to other services by specified ports.
8. _Concurrency_ - Concurrency is advocated by scaling individual processes.
9. _Disposability_ - Fast startup and shutdown are advocated for a more robust and resilient system.
10. _Dev/Prod parity_ - All environments should be as similar as possible.
11. _Logs_ - Applications should produce logs as event streams and leave the execution environment to aggregate.
12. _Admin Processes_ - Any needed admin tasks should be kept in source control and packaged with the application.

## Q24: What are heuristic exceptions? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q25: Why is writing software difficult? What makes maintaining software hard? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q26: What Is Shared Nothing Architecture? How Does It Scale? ⭐⭐⭐⭐⭐

A shared nothing architecture (_SN_) is a distributed computing approach in which each node is independent and self-sufficient, and there is no single point of contention required across the system.

- This means no resources are shared between nodes (No shared memory, No shared file storage)
- The nodes are able to work independently without depending on each other for any work.
- Failure on one node affects only the users of that node, however other nodes continue to work without any disruption.

This approach is highly scalable since it avoid the existence of single bottleneck in the system. In theory, A shared nothing system can scale almost infinitely simply by adding nodes in the form of inexpensive machines.

## Q27: What Is CAP Theorem? ⭐⭐⭐⭐⭐

> CAP theorem states that it is impossible for a distributed software system to simultaneously provide more than two out of three of the following guarantees (CAP): _Consistency_, _Availability_, and _Partition tolerance_.

When we design a distributed system, trading off among CAP is almost the first thing we want to consider. CAP theorem says while designing a distributed system we can pick only two of the following three options:

_Consistency_: All nodes see the same data at the same time. Consistency is achieved by updating several nodes before allowing further reads.

_Availability_: Every request gets a response on success/failure. Availability is achieved by replicating the data across different servers.

_Partition tolerance_: The system continues to work despite message loss or partial failure. A system that is partition-tolerant can sustain any amount of network failure that doesn’t result in a failure of the entire network. Data is sufficiently replicated across combinations of nodes and networks to keep the system up through intermittent outages.

## Q28: What Does Eventually Consistent Mean? ⭐⭐⭐⭐⭐

Unlike relational database property of _Strict consistency_, _eventual consistency_ property of a system ensures that any transaction will eventually (not immediately) bring the database from one valid state to another. This means there can be intermediate states that are not consistent between multiple nodes.

Eventually consistent systems are useful at scenarios where absolute consistency is not critical. For example in case of Twitter status update, if some users of the system do not see the latest status from a particular user its may not be very devastating for system.

Eventually consistent systems can not be used for use cases where absolute/strict consistency is required. For example a banking transactions system can not be using eventual consistency since it must consistently have the state of a transaction at any point of time. Your account balance should not show different amount if accessed from different ATM machines.

## Q29: Is it better to return `NULL` or empty values from functions/methods where the return value is not present?

Returning `null` is usually the best idea if you intend to indicate that no data is available.

An empty object implies data has been returned, whereas returning `null` clearly indicates that nothing has been returned.

Additionally, returning a `null` will result in a null exception if you attempt to access members in the object, which can be useful for highlighting buggy code - attempting to access a member of nothing makes no sense. Accessing members of an empty object will not fail meaning bugs can go undiscovered.

## Q30: Explain the Single Responsibility Principle?

_Single responsibility_ is the concept of a Class doing one specific thing (responsibility) and not trying to do more than it should, which is also referred to as _High Cohesion_.

Classes don't often start out with _Low Cohesion_, but typically after several releases and different developers adding onto them, suddenly you'll notice that it became a monster or _God class_ as some call it. So the class should be refactored.
