## DevOps.
This project will consist of 3 repositorys, this one at .github which as my README.md,poster, research paper  my screen recording for my final yea      
The Frontend and Backend both have their own repositorys with there own worflokws  that automate there deployment hence my reasoning for keeping them seperate.

The project is a 3-tier application consisting of a JSON based authentication API and a websocket chatAPI  split in a register,login chat services and SPA vue application in the frontend, broken down into login and register functionalities along with chat microservices.  
​
This application is divided between two repositories, with both of them fully deployed via a continuous integration and continuous deployment (CI/CD) pipeline written in GitHub Actions. The frontend undergoes automated unit tests, while both the frontend and the services are built with Docker, uploaded to AWS, and automatically deployed through Terraform scripts. These Terraform scripts create the necessary resources on the cluster to make the frontend publicly accessible and enable internal communication with all the services.​  http://k8s-default-vuefront-7672cbf6ed-506806827.eu-north-1.elb.amazonaws.com/#/register
Navigate to the register page, enter a username email and password, note your passsword. use the same username and password to login, navigate to chatRooms. there you can craete,join,leave delete and navigate to one. creating one will add a new chatroom to the view, leaving one will remove you from it but you can still join back, you can only delete it if you created it. Once in there you send and recieve messages and if you send a messeage you are able to delete your own messages after which you can log back out and up until the 6th of may you can come and go as much as you please. This was worked on both mozilla fire fox and braze as of 4/28/25. If for some reason this does not work.

### Docker
Install docker locally, install git, create an empty directory and clone of the backend repostiry and frontend repository in this directory.
Naviagte to the directory of deveop-frontend and run " docker build -t your-image-name -f Docker ."
Then once this completes run "docker run -p 8000:8080 your-image-nameFront" (the port number on the left does not matter so long as its not trying to run on a port something is usng)
after that navgiate to the root directory of deveop-backend and run  " docker build -t your-image-nameBack1 -f Docker.Register-service ."
                                                                       Then run  " docker build -t your-image-nameBack2 -f Docker.Login-service ."
                                                                       Then run  " docker build -t your-image-nameBack3 -f Docker.Chat-service ."
                                                                      "docker run -p 8001:8080 your-image-nameBack1"
                                                                      "docker run -p 8002:8080 your-image-nameBack2"
                                                                      "docker run -p 8003:8080 your-image-nameBack3"
                                                                      
you then navigate to locahost:8000 or whatever port you specficed for your dokcer run command for the frontend. and you can now access the application locally and run the steps above.

### Via coommand line
If the application is unavailabe and docker is not an option, navigate to the root directory in your terminal and run npm install.
Replicate this action 3 more times in the subdirectory of each microservice in the backend.
Then in the frontend run vue serve, you can 
Then navigate into each subdirectory for each service in the backend and rune node index.js.
Vue still start in port 8080 unless recouigred and register,login and chat will start on 3000, 3001 and 3002 respectively.

###
You can also run the automated tests on vue with npm run test:unit.

​
