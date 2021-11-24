# CMPE 281: Project2--Travel-O-Cloud

* University Name: [San Jose State University](http://www.sjsu.edu/)
* Course: [Cloud Technologies](https://catalog.sjsu.edu/preview_course_nopop.php?catoid=12&coid=58375)
* Professor: [Sanjay Garje](https://www.linkedin.com/in/sanjaygarje/)
* Students: [Archana Miyar Kamath](https://www.linkedin.com/in/archana-kamath-018/), [Simran Tanvir Memon](https://www.linkedin.com/in/simran-m-a872a91a1/), [Mounica Kamireddy](https://www.linkedin.com/in/mounica-kamireddy/), [Limeka Dabre](https://www.linkedin.com/in/limekadabre/)

## Project Introduction

Travel-O-Cloud is an one stop application targeted to help users plan a trip or help others to plan a trip by securely login to the application using AWS Login or by using social login providers like Google or Facebook. Users will be able to check weather in a location and book a hotel there using a Chatbot. Users will be able to upload the pictures once they visited any place and store it using our application, share the pictures on facebook and retrieve the pictures from their trip to obtain highlights of locations.

## Demo [URL](https://travelocloud.com/)

## Architecture Diagram

<img width="887" alt="Prjt2_Arch" src="https://user-images.githubusercontent.com/27188674/143139304-d725b428-bf7d-4d88-93dd-cf6b916049a3.png">

## Requirements to run the project locally:

* A free tier AWS account with IAM user access.
* AWS Components required are as mentioned in the following section.
* Softwares Required: Node JS, React JS
* Clone this git repository using ```git clone https://github.com/archana-kamath/travel-o-cloud.git```
* Install backend dependencies at ```travel-o-cloud-backend/``` using ```npm install``` and add a ```.env``` file with IAM user Access ID and Secret key.
* Run ```node app.js``` and server starts running at default port.
* Install frontend dependencies at ```travel-o-cloud-frontend``` using ```npm install```
* Run ```npm start``` and now the application starts running at ```localhost:3000```

## AWS Components Required:

* Route53: This application is hosted on web using Route53, a registered web domain provided by AWS. SSL Cerificate was enabled on this domain by obtaining it from Amazon Cerificate Manager.

* Elastic Beanstalk: Travel-O-Cloud was deployed using Elastic bean stalk, a service to host web applications. It manages the web application by keeping track of important features such as load balancing, auto scaling, health monitoring etc. It comes with EC2 instances by default.

* Reckognition: 

* Amplify: A

* Lex: Using this conversational interface which is voice and text enabled, a chatbot was integared into the application to help users to book hotels. A lambda code hook helps in fulfilling the intent of users.

* S3: S3 bucket was used to store the files in AWS where a life cycle policy was enabled for the bucket in such a way that the files exist in standard S3 for 75 days, then moves to standard IA and stays there for 365 days and then moves to s3 glacier for another 365 days and finally gets deleted. Transfer acceleration was enabled to avoid any delays due to internet routing and speed.

* Cloud Front: Cloud front was enabled for S3 bucket and the files can be accessed and downloaded through lambda edge location. Cloud Front acts as a cache storage. Geo location restriction was enabled for restricted countries.

* Amazon Dynamo DB: 

* Lambda: Lambda function which triggers an SNS email notification was enabled for certain operations on S3 bucket. Email notification will be sent to bucket owners if an event triggers.

* SNS: A notification service which helps users to monitor and track their activity as desired.

* Cloud Watch: A monitoring service to keep track of the health and utilization of resources.

* Code Pipeline: 

* Sage Maker: 



