# Docker

## Regular flowchart (Architecture)
- Single applications <br /> 
Hardware --- Host OS --- Hypervisor --- Guest OS (Image)<br />

- Multiple applications <br />
Hardware --- Host OS --- Hypervisor --- [ Guest OS (Image), Guest OS (Image), Guest OS (Image) ]
                                    
    - Wasting Resources (Hardware, CPU, RAM )            
    - Wasting Money            
                                    
## Container based (Docker)
- Single applications <br /> 
Hardware --- Host OS --- Docker --- Container (Image)<br />

- Multiple applications <br />
Hardware --- Host OS --- Docker --- [ Container OS (Image), Container OS (Image), Container OS (Image) ]

## Approches 
- **Compose and Django** <br /> 
In this approaches, we need to create container frist then create django project. <br />
Container --Create imgae into container ( Django project )
    - Create an empty project directory.
        - You can name the directory something easy for you to remember. This directory is the context for your application image. The directory should only contain resources to build that image.
    - Create a new file called Dockerfile in your project directory. 
        - The Dockerfile defines an application’s image content via one or more build commands that configure that image. Once built, you can run the image in a container.
    - Add the following content to the Dockerfile.

        ````
        FROM python:3
        ENV PYTHONUNBUFFERED 1
        RUN mkdir /app
        WORKDIR /app
        COPY requirements.txt /app/
        RUN pip install -r requirements.txt
        COPY . /app/
        ````
         This Dockerfile starts with a Python 3 parent image. The parent image is modified by adding a new code directory. The parent image is further modified by installing the Python requirements defined in the requirements.txt file.

    - Save and close the Dockerfile.
    - Create a requirements.txt in your project directory.
    - Create a file called docker-compose.yml in your project directory.
    - Add the following configuration to the file.
        ````
        version: '3'

        services: 
        web:
            build: .
            command: python manage.py runserver 0.0.0.0:8000
            volumes: 
                - .:/app
            ports: 
                - "8000:8000"
       
        ````
    - Create the Django project by running the docker-compose run command as follows.
        ````
        docker-compose run web django-admin startproject project_name 
        ````
    - Run the docker-compose up command from the top level directory for your project.
    
    Refrence :  [ Docker docs ]( https://docs.docker.com/compose/django/).

- **Dockerizing Django Web Application**

In this approaches, we need to clone or create django app then need to docerize. <br />
Django app -- Docerize
    - will be add later


       

        





## Helpful command 
- docker ps ( To see running containers )
- docker ps -a ( To view all containers )
- docker image ls ( To view all the images list )
- docker rm container_id ( To remove container from docker )
- docker rmi image_id ( To remove image from docker )
- docker run -it image_id script_name ( To run image file from container )
- docker image pull name_image ( To pull image among docker )
- docker-compose up ( To run the Django projects )
- docker-compose run web django-admin startproject mysite . ( To create project in django in docker container as Image )
- docker exec conatiner_name python manage.py startapp app_name  ( To craete app in django project with inside docker container  )
- docker-compose run service_name python manage.py migrate (To migrate the django app on container )


