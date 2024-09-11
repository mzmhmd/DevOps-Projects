## Installing Jenkins on EC2 with custom port

<p>
<img src="https://github.com/Scar1109/skill-icons/blob/main/icons/Jenkins-Dark.svg" alt="jenkins" width="250" height="250">
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*icemCezVMahlyIQB31tzpA.png" alt="aws-ec2" width="600" height="250">
</p>

Jenkins is a widely-used open-source automation server that streamlines tasks such as building, testing, and deploying software. This guide will outline the steps to install Jenkins on an EC2 instance and access its web interface through a browser on port 8080.

### Step 01: Connect Your EC2 Instance via SSH
The first step is to connect to your EC2 instance via SSH. You can do this by opening a terminal on your local machine and running the following command: ` ssh -i <your-ssh-key> <your-ec2-instance-ip> `<br><br>
Replace `<your-ssh-key>` with the path to your SSH key file and `<your-ec2-instance-ip>` with the public IP address of your EC2 instance.<br>
![1](https://github.com/user-attachments/assets/87ff9c75-9564-4e04-907f-72ea6dbf4508)

### Step 02: Update the package index and install Java
After logging into an EC2 instance, it's a good practice to update the packages using the following command to ensure the system is secure and running with the latest enhancements: ` sudo apt update `<br><br>
Jenkins requires Java to be installed, so use the following command to install Java: ` sudo apt install default-jre `<br>
(I used this command, because this installs the default Java Runtime Environment (JRE), sufficient to run Java applications like Jenkins.)<br><br>
After installing Java, verify the installation by running the following command to check the version: ` java --version `

### Step 03: Install Jenkins
Next, proceed with installing Jenkins by using the following command: <br>
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
Once Jenkins is installed, you can check its current status and ensure it's running correctly by using the following command: ` systemctl status jenkins `

### Step 04: Open port 8080 in the security group associated with the instance
Select the instance where Jenkins is installed, and in the bottom pane, go to the 'Security' tab. Click the name of the security group associated with the instance. In the 'Inbound rules' tab, click the 'Edit inbound rules' button, then click 'Add rule' Select 'Custom TCP Rule' set the 'Port range' to 8080, and in the 'Source' field, enter '0.0.0.0/0' to allow incoming traffic from any IP address.<br><br>
![2](https://github.com/user-attachments/assets/2b8e5c2a-1c17-43e4-828d-11963e333072)

### Step 05: Access Jenkins via a web browser
Now that Jenkins is running on port 8080, we can access it via a web browser. Open your web browser and enter the following URL in the address bar: `http://<your-ec2-instance-ip>:8080`<br>
Replace `<your-ec2-instance-ip>` with the public IP address of your EC2 instance.<br><br>
You should see the Jenkins login page.<br><br>
![3](https://github.com/user-attachments/assets/b9461485-b1c2-43ce-8636-073f319574dc)<br><br>
You can log in with the username admin and the password that you can find on the EC2 instance by running the following command: `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`<br>
Copy the automatically-generated alphanumeric password. On the Unlock Jenkins page, paste this password into the Administrator password field and click Continue.

### Step 06: Customize Jenkins
Recommended selecting Install suggested plugins to `install the recommended set of plugins` based on most common use cases.
The setup wizard shows the progression of Jenkins plugins being installed.<br><br>
![4](https://github.com/user-attachments/assets/27f4b25b-2dfd-4f96-9764-c1b4db618495)
<br><br>
![5](https://github.com/user-attachments/assets/fd5d8626-6ef0-4a1d-b910-c3351df2c431)

### Step 07: Create First Admin User
Enter the details to create admin user and click continue,<br><br>
![image](https://github.com/user-attachments/assets/b3c9109c-49eb-40de-b450-5077825a020d)

### Step 08: Configure Valid DNS (if required)
Jenkins Instance access URL will be printed on the screen that follows. This can be changed with a valid DNS name. For the purpose of our demo, we will leave it as unchanged and click Save and Finish,

### Step 09: Jenkins is now ready, Jenkins now successfully configured
![7](https://github.com/user-attachments/assets/a18d1d41-62be-48e4-8cf9-7d70be0d4a9f)

### Step 10: Let’s click on Start using Jenkins!!
![8](https://github.com/user-attachments/assets/a1358673-f4ec-4fbf-8083-15329b23278e)<br><br>
Jenkins is a powerful automation server that can help you streamline your software development process. In this guide, we have walked through the steps to install Jenkins on an EC2 instance with port 8080 and access it via a web browser. By following these steps, you can take advantage of the many features and benefits of Jenkins to improve your software development process.
