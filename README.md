# AltExam
Altschool Second semester Examination Project
### Documentation: Provisioning the Server, Installing the Web Server, Deploying the HTML Page, and Configuring Networking  

#Here are the steps i took to set up an Ubuntu web server with Apache

**Step 1: Provisioning the Server**
1. I Logged in to AWS using my IAM user credentials.  
2. Created a new EC2 instance named "BabsAlt" and started the instance.  
3. Downloaded the key pair for the instance and noted its location on my local machine.
4. Configured the security group inbound rules to allow:
     *Port 22 ssh from my ip
     *Port 80 http from anywhere  

**Step 2: Connecting to the Server**  
1. Opened the command line (Terminus) and navigated to the folder containing the key pair file.  
   ```bash
   cd ~/Downloads 
   ```  
2. Connected to the EC2 instance via SSH:  
   ```bash
   ssh -i "Alt.pem" ubuntu@ec2-16-16-186-151.eu-north-1.compute.amazonaws.com
   ```  

**Step 3: Updating the Server**
1. Updated and upgraded the server packages:  
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```  
2. Gained root privileges:  
   ```bash
   sudo su
   ```  

**Step 4: Installing the Web Server**  
1. Installed Apache2 on the Ubuntu instance:  
   ```bash
   apt install apache2 -y
   ```  
2. Started and enabled the Apache2 service:  
   ```bash
   systemctl start apache2
   systemctl enable apache2
   ```
   you can also confirm by going to your aws to copy your public ipv4 address and pasting it on a browser.
!browsertest

make sure you change the protocol to http else you'll get an error.

e.g [http://16.16.186.151/] not (https://16.16.186.151/)

**Step 5: Deploying the HTML Page**  
1. Navigated to the web server’s root directory:  
   ```bash
   cd /var/www/html
   ```  
2. Added my custom HTML file (`index.html`) to the directory:  
   ```bash
   nano index.html
   ```  
3. Saved and exited the editor to deploy the page.  

**Step 6: Configuring Networking**  
1. Accessed **freedns.afraid.org** to configure a DNS record for the server’s public IP address.  
2. Created a free subdomain and mapped it to the EC2 instance’s public IP.  

**Step 7: Testing the Deployment**  
1. Accessed the website using the configured subdomain in a web browser to confirm the deployment was successful.  
2. Tested to ensure SSL was correctly assigned to my domain.
Apache was running with my custom index.html landing page. SSL was successfully installed and verified. My web server was accessible via the custom domain at https://web.babs.mooo.com/.

@ Ganiu Babatunde / ALT/SOE/024/1222
