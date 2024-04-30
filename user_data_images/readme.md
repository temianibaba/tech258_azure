# User data
This is an advanced way of creating a virtual machine. By using this option when creating a VM we can run a script without having to SSH into the intance.
## Option in Azure
![alt text](images/image.png)<br>
In the blue highlighted box you can paste your script and it will run once the VM is created, everything should be fine **IF YOUR SCRIPT WORKS!!!**
# Image 
This is a snapshot of the OS or an exact replica of the disk (like a preset).<br>
When creating VM with custom image, the script is set up as a system process so it starts up every time on bootup, the app is not start as it is not a system process (npm commands are not system commands), meaning when using images sometimes you may need a bit of user data to get the app running with the right variables.
1. Set DB_HOST
2. Cd into the app folder
3. Run npm install
4. Run the app with pm2<br>

When using user data, script auto runs after creation of machine, the commands run as fast as putting them in manually, for the image the commands don't have to run (or less commands are run) because everything is installed and configured.<br>
After creating your image, the VM that you captured will be deallocated!!<br>
As long as your VM is allocated it will cost you money, all resources such as CPU and IP are still attached to that machine.<br>
Generalised images delete users home directory.
### Understanding Automation
![alt text](images/image1.png)<br>
The above image shows a graph of how fast an apps runs against time to deploy. As shown by the graph the fastest way to deploy and run an app (that I have learnt at this point of time) is using a preset image.
## Option for image
![alt text](images/image2.png)<br>
After click the option to capture your VM you will be taken to this page, make sure to choose "Capture only a managed image".
## Generalized vs Specialised
- **Generalised:** removes users directory where as a **Specialised** image will keep the user directory
## Errors
**Permissions**: We may have to adjust the permissions of our folder to get the script and app running.
1. chmod -r - Change read/write/execute permissions.
2. chown -r - Change adminuser into owner of app directory.
3. sudo -E - Gives us root user privilege for the command. -E keeps environment variables.

You can login as the root user if these do not work.