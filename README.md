# aws-code-build-code-pipeline
First we create new git hub repoistory where we use this in our build process
# Now go to AWS console and search for Code Build and click on it and here we need to fill the details like
  a. Provide the suitable project name in which project you are working you can provide that.
  b. Provide any description which application you are deploying
  c. Now under source provider you need to choose as Git hub and you can choose option called "Repoistory in my Github account" or "Public   
  repository" and provide the URL
  ![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/223296e6-3bea-490e-bb8d-41373230bf24)

  e. Now you need to choose Connect using OAuth where you github page will pop up and click on confirm
  ![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/72705268-1b02-40e5-abb8-aa1ae778a4b9)

  f. Under Environment choose *Managed image* and select operating system as *ubunutu* and runtime choose as *standard* under image choose always latest *7.0*   under Environtype choose as *Linux* check in 
  *Privilaged box* and under service role we create in IAM codebuild admin access  and we need to create aws systems manager access also where it requires to comminucate
  ![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/0fb7bc5b-5f48-49c4-bdd4-6aad2f3c6d9e)

  
  g. Under build spec we choose *Insert build commands* and we write what is required for our application to be build
   Let's first talk about phases what you want to install here we basically install python we have written as python and we are including any commands while run time
   Now we are talking about Prebuild to this we should use flask our requirements which is present inside the root or subfolder you need to give that *pip install -r requirements.txt*
   this we can find in this github repo with the filename as buildspec.yml

  h. Let's talk about build in this we are using code checkout which is already from Github account you have authenticated to this code build and now we are building the image and push the image
  to docker hub and code analysis you can use image scan one. you need to write some commands to build since we are docker image here we can write like docker build docker login for pushing the image
  docker push and we store this credentials in AWS SSM systems manger.

  i. Now we are not touching CD part since we ar doing only CI part we will add few commands like post build like echo "Build is successfull" after that if you want you can create service role
  else aws will provide it by default, if you have created service you have to refresh the page then only will get reflected role.

  Once done click on create build a rough template has been created for you don't click on start build we need to store the senstive infromation right

# Now we need to move to AWS systems manager for storing senstive parameters follow some standards while writing where we  have to store some hundereds of info if it docker use that naming
convention if it is k8 use that naming convention. here we are using docker so we /sample-app/docker-credentials/registry-url
![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/2d8aa59c-7ef8-4733-8dd1-a0a27e6d147c)

# Once after completion of the above one we need to come home page of code build and click on start build 
![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/41f05f9e-40e1-48db-85ab-99237e1e8452)
Here you can view the Build progress and events and you can observe the logs in cloud watch as well and once after build is complete we need to use code pipline

# Now let's start creating pipeline 
It's basically helps to invoke the code build and starts trigger the build automatically [Assume in place of jenkins]
Go to services search for codepipline and click on create pipeline, these are in to four steps as follows
![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/a9f0019b-0c39-4c5b-a880-d3d2098e7fa5)
We can ignore the step 4 since we are not building the code deploy so we can skip this
Here also we need to choose GitHub latest version and authenticate with GitHub then only our Github repo will be used for any changes you are perfiorming code pipeline will be in sync
![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/d77f02c2-2415-4439-b502-55f2d0147358)
![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/f1dd0180-f7aa-483d-b975-4096ce5b881c) once after filling all the details you will also see
green check mark where it will tell your Github is Ready to connect
In the below third stage you need to select code build and fill the details
![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/234a50ab-b8d1-4103-9477-420997ece99c)
In the fourth stage we can skip since we are not using code deploy, once you are done filling all the four stages you can click on Create pipline. Where you will observe the
AWS code pipline will start and as well it will invoke code build so if you are making any changes to your code it will trigger automatically.









  
