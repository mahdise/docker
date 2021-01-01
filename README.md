# Docker

## Regular flowchart
Hardware --- Host OS --- Hypervisor --- Guest OS (Image)<br />

Multiple applications <br />
Hardware --- Host OS --- Hypervisor --- [ Guest OS (Image), Guest OS (Image), Guest OS (Image) ]
                                    
- Wasting Resources (Hardware, CPU, RAM )            
- Wasting Money            
                                    
## Container based (Docker)
Hardware --- Host OS --- Docker --- Container (Image)<br />

Multiple applications<br />
Hardware --- Host OS --- Docker --- [ Container OS (Image), Container OS (Image), Container OS (Image) ]

## Helpful command 
- docker ps ( To see running containers )
- docker ps -a ( To view all containers )
- docker image ls ( To view all the images list )
- docker rm container_id ( To remove container from docker )
- docker rmi image_id ( To remove image from docker )
- docker run -it image_id script_name ( To run image file from container )
- docker image pull name_image ( To pull image among docker )

