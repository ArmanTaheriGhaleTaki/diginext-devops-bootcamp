# tasks:
## Task: Reverse Proxy
1. Create 3 VM & install Nginx on them
2. Configure all Nginx instances as equal and serve a static page on each of them
3. Specify an instance specific content on each node which enables you to see which one you’re accessing
4. Create a forth VM and install HAproxy on it
5. Configure the HAproxy to answer on a specific URL and balance the load on that Nginx instances
6. Reconfigure the HAproxy to answer on the same URL but on 3 different path which each of them will connect to each Nginx instances
7. Reconfigure the HAproxy to answer on the different URL which each of them will connect to each Nginx instances
## Task: SQL
1. Setup a single MySQL/MariaDB node without any configurations (default configuration). Secure it so you could only be able to connect to it by authentication (root user MUST only be able to connect to it from localhost). Create some databases and within these databases, create some tables and then insert some data in these tables (Play with it).
2. Now lets create a slave node. you need to set some configuration for your master (read where you can put your configurations and what is the best way to do so to make it easy to eyes for read).
3. In which way you desire, corrupt your master node and then change your slave to be act as new master node and then recover your old master node and set it up to be your new slave (switch master & slave roles between your 2 nodes).
4. Now let's use what we did in last task and create a slave for our wordpress service and do as described in section 3 of this task, on this service.
NOTE: It's not important that you want to setup some VMs and install required services OR use docker for this task. I recommend to do both of them or event combine it (master on docker and slave on VM and vice versa)
## Task: noSQL
1. To understand the whole picture, please read with details about raft protocol and also it's important to know which filesystem is suitable for which scenario. About the task itself:
2. Perform required kernel tuning for MongoDB and install a single instance and work a little with it.
3. Setup a replica set cluster with appropriate number of nodes.
4. Like we did with MySQL, create DB, insert, update, ... datat to them. It's better to create a simple python app for this to see how applications communicate with MongoDB.
5. Finally, configure your current replicaset to enable authentication to communicate with MongoDB.




