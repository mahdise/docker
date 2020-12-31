# Docker

## Regular flowchart
Hardware --- Host OS --- Hypervisor --- Guest OS (Image)<br />

Multiple applications
Hardware --- Host OS --- Hypervisor --- [ Guest OS (Image), Guest OS (Image), Guest OS (Image) ]
                                    
-- 
- Wasting Resources (Hardware, CPU, RAM )            
- Wasting Money            
                                    
## Container based (Docker)
Hardware --- Host OS --- Docker --- Container (Image)
Multiple applications
Hardware --- Host OS --- Docker --- Container OS (Image)
                                --- Container OS (Image)
                                --- Container OS (Image)