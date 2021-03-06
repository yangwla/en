## **Border Gateway**

### **Basic Concept**

Border Gateway (BGW) is a gateway used by JD Cloud to bear VPC north-south traffic. Its main function is to realize Intranet interconnection with other external gateways or environments.

Before Border Gateway supports the creation of VPC Attachment function, once a Border Gateway is created, it will be connected with all VPCs in the same region automatically.

As the VPC Attachment function of the Border Gateway is released, newly created Border Gateways won’t connect to any VPC by default, so users need to create "VPC Attachments" to interconnect specified VPC with Border Gateways; for Border Gateways already created, routes, which have already connected to VPC, in the Border Gateway route table is still valid and available, but no other routes to VPC can be created unless VPC Attachment connected to VPC is created.

Currently, Direct Connection, Cabinet Service, VPN Service and VPC Peering function are borne by the Border Gateway.

Border Gateway supports the communication between customer IDC and JD Cloud VPC, the communication between JD Cloud Cabinet Service and JD Cloud VPC, and the communication among several JD Cloud VPCs in the same region.

Under normal conditions, private virtual interfaces/hosted private virtual interfaces connected to the same Border Gateway cannot communicate with each other through the Border Gateway.

JD Cloud resources can be accessed through Border Gateway: All resources in JD Cloud VPC, including Virtual Machines, Container, Load Balancer, Cloud Database, JCS, etc., but the NAT Gateway in VPC cannot be used to unify the Internet exit.

 ### **Border Gateway Route Management**
 
#### Route Table Category

Within JD Cloud, gateways/routers open to users to configure route functions have following route tables:
* ‘Valid Route Table’, which stores actually efficient routes (Local routes automatically generated by the system may be included in the route table). Data packages shall be forwarded based on the route entries in this table, and edit is not supported;
* ‘Static Route Table’, which stores static routes manually added by the user, and edit is supported;
* ‘Transmission Route Table’, which currently stores routes from two sources: One route is automatically transmitted from other gateways and other resources by user configuration (for example, the transmission route table that adds VPC network segment route to border gateway when a VPC attachment is being created) and direct edit is not supported, but transmission route can be changed by modifying the transmission configuration of corresponding resources; another route is learned from dynamic route protocol BGP. BGP route don’t support direct edit in route table, but can be synchronized/converged to BGP route table after edit at route source side (BGP Peer side).

#### Valid routing rules matching order
   
   When the Border Gateway forwards the service data, match item by item according to the routing rules in its valid route table, then forward the packet to the corresponding API or channel according to the next hop information of routing rules. Its basic route matching and forwarding rules are:
   
   Route matching with the longest prefix (the prefix with the longest mask length) takes the priority;

   The equivalent route will hash based on quintuple (TCP/UDP), triple (ICMP) or source/destination IP (other protocol types) of each data packet head so as to forward by selecting different routes of next hop.
   

#### Route source of the valid route table

* Based on the routes and their priorities in the static route table, the transmission route table, select the valid route entries and put them into the valid route table, the actual outgoing traffic will be forwarded according to the route entries in the route table. When forwarding the data package, route matching is handled according to the principles of "valid routing rules matching order" described above.
* Selection principles of route entries are: Routes for different destinations are stored directly, for routes for the same destination, the highest-priority route entry shall be calculated based on the type of Next Hop, route type, and Metric and stored in the valid route table See "Route Priority Calculation Factors" and "Route Priority Level Calculation Rules" as below for the priority calculation method of routes for the same destination.

#### Route Priority Calculation Factors
The calculation of route priority is divided into several different dimensions, and the final priority of this route can be obtained after comprehensive calculation of all dimensions. The calculation dimensions involved include:
* Type of Next Hop, including VPC Attachment, VPN Connection, Private Virtual Interface, Hosted Private Virtual Interface, etc., the priority corresponding to each type of Next Hop is shown in the table below, the lower the value of type of Next Hop, the higher the priority;
* Route Type (Administrative Distance), including Static Route, Internal Communication (VPC Communication), External Protocol Transmission (BGP Route), the value range is: 0~255, the lower the value of the administrative distance, the higher the priority;
* Route Metric is the integer value of the count of hops required and specified by the route (the value range is (: 0~4,294,967,295 (32-bit Integer), the value range of EIGRP, whether it needs to be that big remains to be determined), which is used to select the route that best matches the destination address in the forwarding packet from multiple routes in the route table. The selected route has the minimum count of hops. The number of hops can reflect the count of hops, path speed, path reliability, path throughput and management attributes, which is generated after calculating multiple attributes. The smaller the Metric value, the higher the priority.

#### Route Priority Calculation Rules
* Step 1: Select the route of the highest type of next hop priority. If the unique route entry can be confirmed, return to this route. If there are many routes of the same priority, continue comparing the next factor;
* Step 2: Select the route of the highest route type priority (route protocol management distance). If the unique route entry can be confirmed, return to this route. If there are many routes of the same priority, continue comparing the next factor;
* Step 3: Select the route of the highest Metric priority. If the unique route entry can be confirmed, return to this route. If there are many routes of the same priority, these routes shall be valid routes and forward data package by way of ECMP.


##### Priority Description of Type of Next Hop of Route

|                Name of Gateway of Next Hop                | Priority of Type of Next Hop |
|:--------------------------------------------:|:------------:|
|         VPC Attachment (VPC API)/VPC         |       100        | 
| Private Virtual Interface (Private Virtual Interface/Hosted Private Virtual Interface) |     120        |
|           VPN Connection (VPN Connection)            |   140        |

* Description: The smaller the Type of Next Hop priority value, the higher the route priority.

##### Priority Description of Route Type (Administrative Distance, Administrative Distance of Route Protocol)


|                Route Type                | Route Protocol Priority |
|:--------------:|:--------------:|
|      Static      |       100    |
|      Internal Transmission (VPC Transmission)      |      120       |
|      EBGP      |      150       |
|      IBGP      |      200       |

* Description: The smaller the route Metric value, the higher the priority.

##### Route Metric Priority Description

The smaller the route Metric value, the higher the priority.

Currently, route Metric supports AS_PATH attributes of BGP route protocol, the shorter AS_PATH, the smaller Metric.

