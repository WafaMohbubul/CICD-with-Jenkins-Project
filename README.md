## CI-CD

### 1. Creating our owm Jenkins in AWS
1. Create own instance
2. Select Ubuntu 20.04 lts AMI
3. Select your own VPC 
4. Select your own Security rules
   5. Include port 8080 for Jenkins
6. Launch Instance
7. SSH into Instance via Gitbash inside .ssh folder
8. Once logged in, install Java using following commands:
```commandline
sudo apt update

sudo apt install default-jdk

java -version
```
9. Run commands in Order to install Jenkins:
```commandline
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BA31D57EF5975CA

sudo apt-get update

sudo apt install jenkins
```
10. To get the Jenkins Password, Run Command:
```commandline
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Copy the password.

11. Copy Public IP Address from your instance and paste this is a browser with the Jenkins port 8080
`IP-Address:8080`
12. When instructed, paste the administrator password into Jenkins
13. Select **Install suggested Plugins** and wait for this to install
14. After this has finished, skip the username creation and Finish.

Install SSH Agent:
15. Go to **Manage Jenkins**
16. Click Plugins 
17. Click **Available plugins**
18. Search for **SSH Agent** and **Office 365 Connector**
19. After plugins are successful, return to the Gitbash and copy and paste the commands:
```commandline
sudo su - jenkins
ssh-keyscan github.com >> ~/.ssh/known_hosts
```

### 2. Creating a job
1. Copy and paste private key for **jenkins2**