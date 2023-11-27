![img](https://github.com/CTheTechGuru/Docker-Projects/blob/main/SSH%20Server%20%7C%20Client%20Project%20/Images/maxresdefault.jpg?raw=true)
<h1 align="center">Docker Containerized SSH Server and Client Project</h3>




<!-- PROJECT Details-->
## About The Project
In this project we will create two docker containers. One will be for our openssh server, and the other for our openssh client. 
We will establish a ssh connection from our client and access the server, this is a common practice in the cloud and demonstrates 
how to effectively spin up a docker container for the use off accessing a secure application. 





<!-- Benefits -->


## Benefits of SSH using containers
* Improved Security - SSH Establishes a secure and encypted connection between server and hosts which helps secure and protect the application and data transmitted.

* Ease of management - Easily move from between different environments, making it easy to task, deploy, and scale the application. 

* Collaboration - Multiple team members ability to access an application simultaneously via SSH.

* Scalability - Spin up containers on demand when needed and shutdown when not. Optimizes resources and reduces cost due to flexibility.  

* Portability - Ease of use with multiple cloud providers and does not require dependences due to its packaging, not limited to environment specifics.



## Prerequisites

First we need to download the docker application from docker desktop. https://www.docker.com/products/docker-desktop/

I will use studio visual code as my IDE along with the docker extension, this will also work via shell on MAC, Linux or windows.




## Installation Steps
### Container1 Installation

1. In our terminal we first must download the docker image from docker hub.
    ```sh
     docker pull ubuntu
    ```
3. Now lets verify the docker image was installed. 
    ```sh
    docker images
    ```

    example output
   ```sh
    REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
    ubuntu       latest    xxxxxxxxxxx   7 weeks ago   77.8MB
   ```
5. Create a folder/directory named project1 where we will create our first container and change directory to project1.
    create directory
   ```sh
   mkdir project1
   ```
   ```sh
   cd project1
   ```

  
7. Now we will run the following command which will run the container. 
    ```sh
   docker run -it –name container1 ubuntu
    ```
8. This is our SSH server so we will update the container as well as install SSH.
    Run the following. 
    ```sh
    apt-get update
    apt-get install openssh-server 
    ```
9. We will be editing the configuration file of the SSH server for security purposes. This requires an editor. We will be using nano.
    To install nano run 
    ```sh
    apt-get install nano
    ```

    Open the ssh file 
    ```sh
   nano /etc/ssh/sshd_config/
    ```
    Scroll down the file until you see the following.
   
 ![](https://github.com/CTheTechGuru/Docker-Projects/blob/main/SSH%20Server%20%7C%20Client%20Project%20/Images/d.png?raw=true)

10. Edit - Remove comment 
    PermitRootLogin prohibit-password to
    
    PermitRootLogin yes

    Control S to save, then Control X to exit

13. Now we will start the SSH service.
    ```sh
    service ssh start
    ```
    
   
    Verify service is running  
     ```sh
    service –status-all
    ```
    Example output
    ```sh
     [ - ]  dbus
     [ ? ]  hwclock.sh
     [ - ]  procps
     [ + ]  ssh
     ```

    Now we will create our client container. 


### Container2 Installation


   
1. Create a folder/directory named project2 where we will create our first container and change directory to project2.
    create directory
      
     ```sh

     mkdir project2

     ```
   

     ```sh

       cd project2

     ```

  
3. Now we will run the following command which will run the container. 

   ```sh

   docker run -it –name container2 ubuntu

   ```

5. This is our SSH client so we will update the container as well as install openssh client.
    Run the following. 
```sh
    
    apt-get update
    apt-get install openssh-client

```
   
   
   
### Setup Root Password on SSH Server

1. To startup the container run 
```sh        
    
docker start container1

```    


2. To login and execute run 

```sh
 
docker exec -it container1 bash 

```

3. Now in order for us to connect to the SSHserver we need to configure a password for the root user on our server. 

   Change the password enter 

     ```sh    
   
     passwd root

     ```

     Use password to 123 for simplicity sake. 

4. To get the IP for our server to connect remotely ssh we need the IP address. 

    Enter the following command

    ```sh

    docker inspect container1 | grep IPAddress

    ```
    
    Output should be similar to 172.17.0.2

5. Now our final step is connecting to our server from the client. So we will log back into container2.

### Connect Container2(Client) to Container1(Server)

    ```sh
    run docker start container2
    ```
To login and execute 

    ```sh
    run docker exec -it container2 bash 
    ```

Run 

    ```sh
    ssh root@(ip-address)
    ```
    
You should be prompted with "enter password". 

Enter password that you created and successfully you've established a SSH connection between to docker images. 


<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3
    - [ ] Nested Feature

See the [open issues](https://github.com/github_username/repo_name/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Your Name - [@twitter_handle](https://twitter.com/twitter_handle) - email@email_client.com

Project Link: [https://github.com/github_username/repo_name](https://github.com/github_username/repo_name)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* []()
* []()
* []()

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
