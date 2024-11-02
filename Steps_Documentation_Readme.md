Challenges
1) netifaces lib was not added and also netifaces plus supports the advance version of python so added that
2) During creating docker image for app corrrected a lot of intentional errors such unmatched worker directory in Dockerfile
3) the nginx Dockerfile  was containing a lot errors fixed that wrong port declarations were there and wrong directory which doest not exist in master folder
4) then after bulding both images inside docker-compose under services changed the intentional changes 
5) once i named nginix inside Dockerfile unkownlingly so it was contardicting the compose file so after reviewing i fixed it                                                   
6) in order to run both container i runned docker compose up but intially network was not created then i have to do some changes in compose file then buils and run agian
7) I was thinking of scale up the app so intailly it was showing error on running docker compose then i found inside compose the host port is explicitly binded so i removed it then i runned so it was running with assinged random ports of host all 3
8) i make changes in app.py to show container id each time i hit refresh in case of scale up and using nginix proxy server as laodbalancer but intially it was not reflecting on hiting url so i have to rebuild the image of app.py fro sccratch then to docker compose run
 
HERE ARE SOME SCREENSHOTS TO SHOW I PROCEDED IN A MINMALISTIC WAY

flask app runned locally
![alt text](<screenshots_ignore/1.png>)

Build both images
![](<screenshots_ignore/2.png>)

Run app.py container binded to 8000 local hos
![](<screenshots_ignore/3.png>)
running docker images with proxy
![](<screenshots_ignore/4.png>)
nginx logs
![](<screenshots_ignore/5.png>)

then i thought if there is nginx why not load balance it
bulid images scled to 3
![](<screenshots_ignore/6.png>)
refresh 1
![](<screenshots_ignore/7.png>)
refresh 2
![](<screenshots_ignore/8.png>)
local host and port binding
![alt text](<screenshots_ignore/9.png>)



Challenges with cloud deployemt on AWS EC2 INSTANCE
1) No i want to write it first the sudo command always i forget
2) Here after ssh client login i was able to communicte with my machine server only thing that make me sick was setting up inbound rules in secrity sections wher i have to add 8000 port for app and 22 for ssh and 80 for nginx
3) i first pushed code through local machine on git hub then clone to my ec2 machien then installed docker and everything was same afterwards to localmachine
    

     my public ip is 65.1.248.56 
  
     my public ipv4 dns ec2-65-1-248-56.ap-south-1.compute.amazonaws.com       
  
  
     IT Will remain up for you
   
    Running ec2 instance
![alt text](<screenshots_ignore/10.png>)

  cloned from git
  ![alt text](<screenshots_ignore/11.png>)

  build only app.py image and runned it on http://<ec2-public-ip>:8000
  ![alt text](<screenshots_ignore/12.png>)

  docker compose build

  ![alt text](<screenshots_ignore/13.png>)
  
   # note that here i have specified port of machine to inside docker-compose as i was using  bridge driver isloated from host which diiferent from pushed code on github

  ![](<screenshots_ignore/14.png>)      

  The log entry shows a 404 for the /favicon.ico, which means that when the browser attempts to retrieve the favicon (the little icon that appears in the browser tab), it's not found.it can be resolved by adding a favicon.ico file to flask app directory                             


  