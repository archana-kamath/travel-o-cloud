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

* Image Rekognition: This service is used in application to recognize the objects in the uploaded image which further helps to filter the images while searching. A lambda code hook gets enabled when user uploads images.

* Cognito & Amplify: Login and authentication was done via Amplify auth and social login provision for google and facebook was enabled using federated sigin capability.

* Lex: Using this conversational interface which is voice and text enabled. Amplify interactions which uses Lex was used to integrate chatbot into application to book hotels. A lambda code hook helps in fulfilling the intent of users. 

* S3: S3 bucket was used to store the files in AWS where a life cycle policy was enabled for the bucket in such a way that the files exist in standard S3 for 75 days, then moves to standard IA and stays there for 365 days and then moves to s3 glacier for another 365 days and finally gets deleted. Transfer acceleration was enabled to avoid any delays due to internet routing and speed. Replica of the used bucket was configured in different region to enable disaster recovery.

* Cloud Front: Cloud front was enabled for S3 bucket and the files can be accessed and downloaded through lambda edge location. Cloud Front acts as a cache storage. Geo location restriction was enabled for restricted countries.

* Amazon Dynamo DB: A NoSQL DB used to store user details and corresponding image uploads.

* Lambda: A lambda function which gets triggered once user uploads images to S3 bucket and sends emails to application owner. 

* SNS: A notification service which helps application owner to monitor and track users activity.

* Cloud Watch: A monitoring service to keep track of the health and utilization of resources.

* Sage Maker: A service used to build, train and deploy ML models. This application can be further enhanced to help users in recommending hotels based on location and customer reviews.

* Code Pipeline: A CI/CD service which enables continuous integration and delivery when ever a code commit occurs in github and S3. An updated deployed version is delivered to Elastic bean stalk application.



