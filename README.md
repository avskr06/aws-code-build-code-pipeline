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
   Now we are talking about Prebuild to this we should use flask our requirements which is present inside the root or subfolder you need to type likw wise 
