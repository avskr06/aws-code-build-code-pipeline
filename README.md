# aws-code-build-code-pipeline
First we create new git hub repoistory where we use this in our build process
Now go to AWS console and search for Code Build and click on it and here we need to fill the details like
  a. Provide the suitable project name in which project you are working you can provide that.
  b. Provide any description which application you are deploying
  c. Now under source provider you need to choose as Git hub and you can choose option called "Repoistory in my Github account" or "Public   
  repository" and provide the URL
  ![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/223296e6-3bea-490e-bb8d-41373230bf24)

  e. Now you need to choose Connect using OAuth where you github page will pop up and click on confirm
  ![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/72705268-1b02-40e5-abb8-aa1ae778a4b9)

  f. Under Environment choose *Managed image* and select operating system as *ubunutu* and runtime choose as *standard* under image choose always latest *7.0*   under Environtype choose as *Linux*
  ![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/fd03b80f-4e6d-4ab4-9c51-9d0df431818e)

  g. Under build spec we choose *Insert build commands* and we write what is required for our application to be build
   Let's first talk about phases what you want to install here we basically install python we have written as python and we are including any commands while run time
   Now we are talking about Prebuild to this we should use flask our requirements which is present inside the root or subfolder you need to give that *pip install -r requirements.txt*

  h. Let's talk about build in this we are using code checkout which is already from Github account you have authenticated to this code build and now we are building the image and push the image
  to docker hub and code analysis you can use image scan one. you need to write some commands to build since we are docker image here we can write like docker build docker login for pushing the image
  docker push and we store this credentials in AWS SSM systems manger.

  i. Now we are not touching CD part since we ar doing only CI part we will add few commands like post build like echo "Build is successfull" after that if you want you can create service role
  else aws will provide it by default, if you have created service you have to refresh the page then only will get reflected role.

  Once done click on create build a rough template has been created for you don't click on start build we need to store the senstive infromation right

Now we need to move to AWS systems manager for storing senstive parameters follow some standards while writing where we  have to store some hundereds of info if it docker use that naming
convention if it is k8 use that naming convention. here we are using docker so we /sample-app/docker-credentials/registry-url
![image](https://github.com/avskr06/aws-code-build-code-pipeline/assets/144780588/2d8aa59c-7ef8-4733-8dd1-a0a27e6d147c)



  
