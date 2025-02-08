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

1. go with default options and need to create declaritive pipeline
