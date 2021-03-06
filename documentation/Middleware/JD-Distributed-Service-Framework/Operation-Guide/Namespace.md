# Namespace
Namespace refers to an abstract collection of a group of resources and objects, used for resource isolation. A user can create several namespaces under the same VPC.

For example, a user can respectively create 3 namespaces in the same VPC for the development environment, test environment and production environment according to project demands; in addition, in each environment, resources and applications are separated to each other.
 


## Operation Steps

### Create

1. 	Log in the JD Distributed Service Framework Console. Click **Namespace** on the left side navigation bar and enter the namespace list page.

2. 	Click **Create Namespace** on the top of the list and log in the creation page.

3.	 Set service information, click **Buy Now** button and complete creation.

**Description:**

-  The registration center will be synchronously generated to manage all service registration and discovery under the namespace.

![](../../../../image/Internet-Middleware/JD-Distributed-Service-Framework/np-create-1.png)

### Delete

1. 	Log in the JD Distributed Service Framework Console.	Click **Namespace** on the left side navigation bar and enter the namespace list page.

2. For the namespace to be deleted, click **Delete** on the operation bar.


**Description:**

1. Before deleting a namespace, please clear all applications under such namespace, otherwise, it cannot be deleted.

2. Before deleting the data, a user needs to well complete data backup work on his/her own.
