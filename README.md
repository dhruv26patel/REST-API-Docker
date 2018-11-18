# REST Service Docker
This is a REST service implementation using Python and Flask library. The service will be hosted on AWS Ubuntu Server. 

### Prerequisits
1. Lauch a Ubuntu Ec2 instance which can be a t2.mico (free tire). Make sure you have allowed the ports which you intent to run couchdb on. For purpose of this example we will be using port 5986.
2. SSH into the ec2 instance using Public DNS name. 
3. Install docker using the following steps: 
```
sudo apt-get update
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 9DC858229FC7DD38854AE2D88D81803C0EBFCD88
sudo apt-add-repository 'deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial main stable'
sudo apt-get update
sudo apt-get install -y docker-ce
```
4. To ececute Docker commands we need to create a user and add it to the docker group which can be done using the folowing steps
```
sudo adduser <username>
sudo usermod -aG docker <username>
```
5. You can change between user using the following commands and whoami (command which display the current user) 
```
su - <username>
whoami
```
6. 
