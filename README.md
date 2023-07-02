# Deploy-a-Game-using-Docker-into-AWS Elastic beanstalk
DevOps Project

The game is : 2048 game 

source code : https://github.com/gabrielecirulli/2048

- create a Docker file that will create a Docker container
- Deploy the docker container into AWS Elastic Beanstalk

## Creating a Docker file:

```
FROM ubuntu:22.04

RUN apt-get update -y

RUN apt-get install -y nginx zip curl

RUN echo "daemon off;" >>/etc/nginx/nginx.conf

RUN curl -o /var/www/html/master.zip -L https://codeload.github.com/gabrielecirulli/2048/zip/master

RUN cd /var/www/html/ && unzip master.zip && mv 2048-master/* . && rm -rf 2048-master master.zip

EXPOSE 80

CMD ["/usr/sbin/nginx","-c","/etc/nginx/nginx.conf"]

```
- Building the image : `docker build -t 2048-game .`
- Running the image: `docker run -d -p 80:80 2048-game`

Now, we can test the localhost: 

![image](https://github.com/balajisomasale/Deploy-a-Game-using-Docker-into-AWS-Elastic-beanstalk/assets/35003840/baed6468-f2d2-4c4b-89ff-8c17eb7fb7aa)

## Integrating with AWS Beanstalk: 

### What is Amazon Elastic Beanstalk? 
- End-to-end web application management.
- Amazon Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS.

Get started with quick steps: Easily deploy your web application in minutes.

- You simply upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, and automatic scaling to web       application health monitoring, with ongoing fully managed patch and security updates

![image](https://github.com/balajisomasale/Deploy-a-Game-using-Docker-into-AWS-Elastic-beanstalk/assets/35003840/b680f4a8-e2e3-419b-b5cf-d03ec570ee1c)

we need to select `Docker` in platform: 

![image](https://github.com/balajisomasale/Deploy-a-Game-using-Docker-into-AWS-Elastic-beanstalk/assets/35003840/8fabc594-2460-42b2-a5bd-6116b86f1c82)

- choose Upload your code(browse the Dockerfile path location)

![image](https://github.com/balajisomasale/Deploy-a-Game-using-Docker-into-AWS-Elastic-beanstalk/assets/35003840/426f4c46-850d-4c4f-a7b7-7088b4314748)

we can skip all the next steps : skip to review and submit it 

![image](https://github.com/balajisomasale/Deploy-a-Game-using-Docker-into-AWS-Elastic-beanstalk/assets/35003840/16201810-ed75-4d0e-a37c-2f1acc77510a)

![image](https://github.com/balajisomasale/Deploy-a-Game-using-Docker-into-AWS-Elastic-beanstalk/assets/35003840/6e1e8347-11e7-413e-a76f-78d95cc0c1d6)

![image](https://github.com/balajisomasale/Deploy-a-Game-using-Docker-into-AWS-Elastic-beanstalk/assets/35003840/dcb56ae6-1524-4698-b3af-cc5dc4cf9ff7)


------------- EOF --- 
