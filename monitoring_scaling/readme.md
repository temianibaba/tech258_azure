# Monitoring
## Different Approaches
This image shows different approaches to monitoring and the flow of each approach. As shown the best approach would be to automatically scale the VM when an alert is triggered.<br>
![alt text](images/image.png)
## Setting up a dashboard
After setting up your VM, in the monitoring section in overview you can create a dashboard by clicking on the pin icon as shown. You will have to name the dashboard!<br>
![alt text](images/image3.png)
You can access your dashboard by searching for the "Dashboard Hub" in the search bar.<br>
![alt text](images/image4.png)
After entering your dashboard you will be able to edit it however you like<br>
![alt text](images/image5.png)
## Load Testing
You are able to test your VM and how it reacts to requests by using the commands below. Apache bench is the package that will be installed to do these get requests.
```bash
# Install apache bench
sudo apt-get install apache2-utils

# use VMs public IP
172.187.91.219

ab -n 1000 -c 100 http://172.187.91.219/

# -n is number of requests
# -c is speed

ab -n 10000 -c 200 http://172.187.91.219/

ab -n 20000 -c 300 http://172.187.91.219/

ab -n 40000 -c 300 http://172.187.91.219/
```
# Alert Management
There are two ways to create an alert rule: 
1. You can do it via your dashboard on the metric being tracked
2. You can go to alerts in the monitoring section of you VM
Either way you will come to this screen where you have to configure the alert settings
![alt text](images/image1.png)
![alt text](images/image2.png)

# Scaling 
Scaling up and down increases size of VM.<br>

VM scale sets can increases or decreases the number of VMs you can scale out or in.<br>

This image shows how a VM scale set is made and the thought process behind it.<br>
By starting off from a basic hard disk file you can create a custom image with the right provisions (files) to run your app in your instance.
![alt text](images/image6.png)
### Take aways
- You need to configure the VM scale set's custom autoscale. According to your own criteria you can set the minimum default and max number of machines, you can also change therequired CPU load to start the autoscaling
- You need to create a custom image
- **High availability** comes from your VMs being in different zones at the same time and launches a new instance if there is a lot of traffic. The default/ minimum of 2 VMs gives robustness
- **High scalability** comes from the VM scale set adapting when the set CPU load is reached
- This happens within the public subnet
- An external Load balancer, organises internet traffic depending on the individual VMs capacity.
- Custom autoscale CPU threshold takes an average and scales instances accordingly.


![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
![alt text](image-4.png)
![alt text](image-5.png)
![alt text](image-6.png)
![alt text](image-10.png)
![alt text](image-7.png)
![alt text](image-8.png)
![alt text](image-9.png)
![alt text](image-11.png)
![alt text](image-12.png)