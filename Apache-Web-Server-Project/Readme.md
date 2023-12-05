<div align="center">
    <img src="https://github.com/CTheTechGuru/Docker-Projects/blob/main/Apache-Web-Server-Project/1606047804023.png">
</div>
                                   



<!-- PROJECT Details-->
## About The Project
What is a Apache Server you may ask? 
It's an open source web server which configures and hosts web applications online and locally using localhost as the medium.

How does this architecture work?
* An HTTP request is sent from the users web browser to the apache web server ran in our docker container.
* The docker container is running on the docker host, which runs the docker engine.
* The docker engine communicates with the docker API, which is used to manage containers and images. 
* The Apache webserver handles incoming http requests and return the appropriate responses. 
* The Apache web server also listens on specific ports. 


<!-- Benefits -->


## Benefits of a Containerized Apache Webserver 
* Isolation - Isolated environment which is not impacted by host system. 

* Consistency - The packaging of a docker container with its dependencies ensures the application can be run consistently across different environment.(prod | staging)

* Collaboration - Multiple team members ability to access an application simultaneously via SSH.

* Scalability - Spin up containers on demand when needed and shutdown when not. Optimizes resources and reduces cost due to flexibility.  

* Security - Makes it harder for attackers to due to containers not being use on the host machine and in a seperate isolate environment. 


## Prerequisites

First we need to download the docker application from docker desktop. https://www.docker.com/products/docker-desktop/

I will use studio visual code as my IDE along with the docker extension, this will also work via shell on MAC, Linux or windows.




## Installation Steps
### Create Folder and dockerfile for project.

1. Create new folder for project named ApacheWebServer and cd into folder. 

2. Create a docker file from the File tab.

![](https://github.com/CTheTechGuru/Docker-Projects/blob/main/Apache-Web-Server-Project/5.png)

2. Go to settings at bottm left and change autosave to onFocusChange to save without losing progress.

### Create dockerfile configuration 
2. Open docker file in VScode. 

    Enter following config code
    ```
    FROM ubuntu:latest
    Run apt-get update && apt-get install -y apache2
    EXPOSE 80
    CMD ["apache2ctl", "-D", "FOREGROUND"] 
    ```
3. Now log into terminal in VSCode, ensure you are in the directory of the 
    the docker file and run the following command. 
    
    *example docker build -t (name-of-image) .*

    ``` docker build -t my-apache-image . ```

### Run container image
1. Now we will create the container from the image in we created. 
   Replace   _my-apache-image_ with the name of your image if it is different. 
   
    Run
    
    ```
    docker run -p 80:80 my_apache_image
    ```

3. Now we will verify our apache web server is working by connecting to 
    localhost in our web browser. We should get the default Apache default page. 

    ```Output example```


   
![](https://github.com/CTheTechGuru/Docker-Projects/blob/main/Apache-Web-Server-Project/4.png)



   
<!-- CONTACT -->
## Contact

Cordelra Lowman - Cordelra_Lowman@yahoo.com

Project Link: (https://github.com/CTheTechGuru/Docker-Projects/tree/main/SSH%20Server%20%7C%20Client%20Project%20))

<p align="right">(<a href="#readme-top">back to top</a>)</p>






<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
