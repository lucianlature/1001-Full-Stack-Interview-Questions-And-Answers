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

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q5: What Is Load Balancing? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q6: What Is Sticky Session Load Balancing? What Do You Mean By "Session Affinity"? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q7: What Is Fail Over? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q8: What Do You Mean By High Availability? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q9: "People who like this also like... ". How would you implement this feature in an e-commerce shop? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

## Q10: What Is ACID Property Of A System? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q11: What Is Middle Tier Clustering? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q12: How Do You Update A Live Heavy Traffic Site With Minimum Or Zero Down Time? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q13: Explain Blue-Green Deployment Technique ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q14: How can you keep one copy of your utility code and let multiple consumer components use and deploy it? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q15: What does SOLID stand for? What are its principles? ⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q16: Defend the monolithic architecture. ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q17: What Is Sharding? ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q18: What Is IP Address Affinity Technique For Load Balancing? ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q19: What Is BASE Property Of A System? ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q20: Explain threads to your grandparents ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q21: Why layering your application is important? Provide some bad layering example. ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q22: Why should you structure your solution by components? ⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q23: Are you familiar with The Twelve-Factor App principles? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q24: What are heuristic exceptions? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q25: Why is writing software difficult? What makes maintaining software hard? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q26: What Is Shared Nothing Architecture? How Does It Scale? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q27: What Is CAP Theorem? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>

#### Q28: What Does Eventually Consistent Mean? ⭐⭐⭐⭐⭐

Read answer on 👉 <a href='https://www.fullstack.cafe'>FullStack.Cafe</a>
