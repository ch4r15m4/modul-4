## KELOMPOK 14

#### Axel & Charisma

- First, make 2 copies of containers, and then start

![Screenshot (546)](C:\Users\axel\Downloads\z file\z file\Screenshot (546).png)

![Screenshot (547)](C:\Users\axel\Downloads\z file\z file\Screenshot (547).png)

- Next, open ubuntu_php7.4_2 and change the IP address to 10.0.3.111/24. Do the same thing on ubuntu_php7.4_3, change the IP address to 10.0.3.121

![Screenshot (548)](C:\Users\axel\Downloads\z file\z file\Screenshot (548).png)

- Go to lxc_php7_2.dev and change the server name


![Screenshot (550)](C:\Users\axel\Downloads\z file\z file\Screenshot (550).png)

![Screenshot (552)](C:\Users\axel\Downloads\z file\z file\Screenshot (552).png)

- Restart nginx then curl it. Repeat the same steps for 'ubuntu_php7.4_3'

![Screenshot (553)](C:\Users\axel\Downloads\z file\z file\Screenshot (553).png)

![Screenshot (554)](C:\Users\axel\Downloads\z file\z file\Screenshot (554).png)

- Still same with ubuntu_php7.4 we need start all container

![Screenshot (556)](C:\Users\axel\Downloads\z file\z file\Screenshot (556).png)

- Go to debian_php5.6_2 and change IP address to 10.0.3.112, then go to debian_php5.6_3 and change IP address to 10.0.3.122

![Screenshot (557)](C:\Users\axel\Downloads\z file\z file\Screenshot (557).png)

- Go to /etc/hosts and register lxc_php5_2.dev

![Screenshot (558)](C:\Users\axel\Downloads\z file\z file\Screenshot (558).png)

- Change the name server, then do the same thing for debian_php5.6_3. Dont forget to restart the container

![Screenshot (559)](C:\Users\axel\Downloads\z file\z file\Screenshot (559).png)

- Register all of the container to /etc/hosts (in vm)

![Screenshot (571)](C:\Users\axel\Downloads\z file\z file\Screenshot (571).png)

- Run the jmeter.  Change the number of threads from user access from 50, 100, 150

![Screenshot (572)](C:\Users\axel\Downloads\z file\z file\Screenshot (572).png)

![Screenshot (573)](C:\Users\axel\Downloads\z file\z file\Screenshot (573).png)

![Screenshot (574)](C:\Users\axel\Downloads\z file\z file\Screenshot (574).png)

![Screenshot (575)](C:\Users\axel\Downloads\z file\z file\Screenshot (575).png)

![Screenshot (576)](C:\Users\axel\Downloads\z file\z file\Screenshot (576).png)

![Screenshot (577)](C:\Users\axel\Downloads\z file\z file\Screenshot (577).png)

![Screenshot (578)](C:\Users\axel\Downloads\z file\z file\Screenshot (578).png)

![Screenshot (579)](C:\Users\axel\Downloads\z file\z file\Screenshot (579).png)

![Screenshot (580)](C:\Users\axel\Downloads\z file\z file\Screenshot (580).png)

![Screenshot (581)](C:\Users\axel\Downloads\z file\z file\Screenshot (581).png)

- Then we went back to VM than go to

  ```
  nano /etc/nginx/sites-available/vm.local
  ```

- To add upstream landing, php5, and php7

![Screenshot (582)](C:\Users\axel\Downloads\z file\z file\Screenshot (582).png)

- Change the proxy_pass

![Screenshot (583)](C:\Users\axel\Downloads\z file\z file\Screenshot (583).png)

- Then we go back to the jmeter and redo it

![Screenshot (584)](C:\Users\axel\Downloads\z file\z file\Screenshot (584).png)

![Screenshot (585)](C:\Users\axel\Downloads\z file\z file\Screenshot (585).png)

![Screenshot (586)](C:\Users\axel\Downloads\z file\z file\Screenshot (586).png)

![Screenshot (587)](C:\Users\axel\Downloads\z file\z file\Screenshot (587).png)

![Screenshot (588)](C:\Users\axel\Downloads\z file\z file\Screenshot (588).png)

![Screenshot (589)](C:\Users\axel\Downloads\z file\z file\Screenshot (589).png)

![Screenshot (590)](C:\Users\axel\Downloads\z file\z file\Screenshot (590).png)

![Screenshot (591)](C:\Users\axel\Downloads\z file\z file\Screenshot (591).png)

![Screenshot (592)](C:\Users\axel\Downloads\z file\z file\Screenshot (592).png)

##### Analysis

Below are the results when using a load balancer and not using a load balancer

- when there are 50 users accessing our web, if we don't use a load balancer then the average time users access our web is
  - landing : 785 ms = 0.79 s
  - blog : 360 ms = 0.36 s
  - app : 438 ms = 0.44 s
- when we use load balancer, then
  - landing : 686 ms = 0.69 s
  - blog : 229 ms = 0.23 s
  - app : 225 ms = 0.23 s

Here we can find out that the average time a user accesses our web is faster using a load balancer than if they don't use a load balancer. For throughput or the number of users accessing our web, namely:

- When there are 50 users accessing our web, if we don't use a load balancer, the number of users accessing our web is
  - landing : 42 users / second
  - blog : 43 users / second
  - app : 47 users / second
- when using a load balancer, then
  - landing : 54 users / second
  - blog : 84 users / second
  - app : 77 users / second

Here we can see that by using a web load balancer more users can be accessed in 1 second

In conclusion, if we use a load balancer, the time required is faster and the number of users accessing our web is more than if we do not use a load balancer.