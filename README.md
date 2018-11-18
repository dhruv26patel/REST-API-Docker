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
6. The files require to run the rest service successfull is in the app folder and we will be going though the Dockerfile which is the most imporntant file
```
FROM ubuntu:latest
RUN apt-get update -y
RUN apt-get install -y python-pip python-dev build-essential
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
ENTRYPOINT ["python"]
CMD ["hello.py"]
```
In this dockerfile we are choosing ubuntu as type of OS and installing python on it. We are copy the file to an app folder which is specificed as a working directory. Then we mention the entrypoint for the application and the command that we need to run which is the hello.py file. 

7. To build the docker we use the following command: 
```
docker build -t flask-example:latest .
```

8. To run the docker we use the following command which exposes port 5000 from docker and also the host machine 
```
docker run -d -p 5000:5000 flask-example
```

9. You can run the command below to verify if the container is running on the right port 
```
docker ps -a 
``` 

10. You should now be able to use the instance Public IP IPv4 address and append the port and be able to see the welome page.
```
<Public IP IPv4>:5000
```

