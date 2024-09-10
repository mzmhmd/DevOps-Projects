## Installing Jenkins on EC2 with custom port

<p>
<img src="https://github.com/Scar1109/skill-icons/blob/main/icons/Jenkins-Dark.svg" alt="jenkins" width="250" height="250">
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*icemCezVMahlyIQB31tzpA.png" alt="aws-ec2" width="600" height="250">
</p>

Jenkins is a widely-used open-source automation server that streamlines tasks such as building, testing, and deploying software. This guide will outline the steps to install Jenkins on an EC2 instance and access its web interface through a browser on port 8080.

### Step 01: Connect Your EC2 Instance via SSH
The first step is to connect to your EC2 instance via SSH. You can do this by opening a terminal on your local machine and running the following command:
` ssh -i <your-ssh-key> <your-ec2-instance-ip> `<br><br>
Replace `<your-ssh-key>` with the path to your SSH key file and `<your-ec2-instance-ip>` with the public IP address of your EC2 instance.<br>
![1](https://github.com/user-attachments/assets/87ff9c75-9564-4e04-907f-72ea6dbf4508)
