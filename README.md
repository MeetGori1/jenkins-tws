# jenkins-tws
**Set up Jenikins on Cloud Incatance**

1. create instance and install java:

```
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
```

2. to install jenkins
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update

sudo apt-get install jenkins
```

3. to start jenkins when instance started
```
sudo systemctl enable jenkins
```

4. jenkins runs on port 8080 need to update firewall rules according
5. to check jenkins is runnig or not
   ```
     sudo systemctl status jenkins
    ```
7. first time jenkins needs default password, by accessing it by using this in instance 
 ```
   sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
---

**Set up Pipelines**

1. Create Other Instance for agent
   -- set up in second instace
   1. neeed to install java manually in it
   2. ssh into master instance and create public and private key pair using ssh
    ```
    cd ~/.ssh
    ssh-keygen
    ```
    3. private ssh key needed in master instance, need to add public key in agent instance
    4. in agent instance add master instance public key in "authorised_key" file 

2. in master instance select set up agent
3. put "/home/username" in root directory section
4. add relevant label
5. in launch method select "launch via ssh"
    - in host section add instance's public ip address
    - add new credentials
       - in kind select "ssh user name with private key"
       - fill id, description, username,
       -select private key and put private ssh key of master instance
6. in Host Key Verification Strategy select "non verifying verification statergy" and save

   
