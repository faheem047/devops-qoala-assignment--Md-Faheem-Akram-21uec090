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


![alt text](<Screenshot (524).png>)
flask app runned locally

![Build both images](<Screenshot (526).png>)

![Run app.py container binded to 8000 local host](<Screenshot (527).png>)

![running docker images with proxy ](<Screenshot (531).png>)

![nginx logs](<Screenshot (532).png>)

then i thought if there is nginx why not load balance it

![bulid images scled to 3](<Screenshot (533).png>)

![refresh 1](<Screenshot (535).png>)

![refresh 2](<Screenshot (536).png>)

![local host and port binding](<Screenshot (537).png>)