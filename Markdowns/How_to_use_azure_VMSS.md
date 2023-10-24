# Azure VMSS (virtual Machine Scale Set)

- here we will learn `how to sale the number of build agent` using `Azure VMSS` in `Azure Devops`

- `Azure VMSS` is an `resource` in `Azure`, that allow us to create the `group of virtual machine` and then `scale out` and `scale in` from `0 to 100` vm depending on the `load that we got from the Virtual Machine`

- this will be useful when
  
  - when we have `CICD pipeline` which can `run` in `parallel`
  
  - when we have `multiple jobs and stages` that run `in parallel` and we want to `reduce the time needed` by the `pipeline` in order to run
  
- `Azure VMSS` can be `cost effective solution` as we have to `pay for what we use` , if the `pipeline` need `10 Azure VM` to run the `pipeline` for `5 minutes` then we need to `pay only for that consumption`
  
  - if later we don't need the `pipeline` then it can `scale down` to `0 VM` as well , `at that time we are saving cost`
  

- **How to create Azure VMSS and associate that with Azure Pipeline** 
  
  - go to `portal.azure.com` &rarr; `select azure Virtual Machine Scale Set` &rarr; `we ned to select the subscription` &rarr; `we need to select the resource group or create a new resource group`
  
  - make sure to select the `orchestration as uniform not flexible`
  
  - we need to provide the name to the `Azure VMSS` and then we need to select the region as `West Europe` & Availability Zone(which is not mandetory) as `None` in this case
  
  - we need to select the `instance details` which type of `instance` that we might need , Here we can select the `ubuntu Server 18.04 LTS-Gen1` &rarr; select the `VM architecture` as well 
  
  - in the `instance details` we cam select any `Linux/Windows` image, even we can select `any image by browsing through it`
  
  - we can select the `Size` as `Standard B2S` which is very cost effective in this case
  
  - then we can select the `Authentication type` as `SSH public key(default) or password`  and provide the `username` and select the `keypair name` for the same 
  
  -  then we can move to the `next(Disk)` in this case
     
     - here we can select the `OS Disk Type` as below 
       
       - `Premium SSD`
       
       - `standard SSD`
       
       - `Standard Disk`   
    
  - then we can move to the `Networking Section`
    
    - select the `virtual Network` where by default it `Azure` will create the `new Virtual Network` , if we have a `private Virtual Network` then we can use that as well in this case
    
  -  then we can sen select the `Scaling` option 
     
     - here can select the `scaling policy` as `Manual`
     
     - also the `initial instance count` which default to `2` by default
     
  -  then we can move on to the `Management Section`
     
     - here we need to select the `Enable OverProvisioning` option as `enabled` in this case 
     
     - here we can see the `Automatic OS Upgrade` in this case as well  
     
  -  then we can move onto the `Health` section which will be keep in `default` 
  
  - also in this case we need to select the `Advance` Section
    
    - we need to selet the `spreading alogorithm` as `Fixed Spreading` with `fault domain count` as `count of 5`

  - then we need to `review and create` which will validate the `configuration template`
  
  - once `validated` and `validation successful` then we can `select` the `create` option for the same 
  
  - this will `prompt to download the key pair` and then we can `see the Azure VMSS resource` getting created 
  
  - if we go to the `Azure VMSS`  then we can see the `instnce` and `scaling` and the `update policy` as `Existing Manual Upgrade` in this case 
  
  - as we have selected the `initial instance count` as `2` in the `Scaling` then we can see the `2 Vm been currently running`
  
  - here we have selected the `Scaling Policy` as `manual` hence we can see the `manual scale` as `scaling policy` in here

  - here in case of the `manual scaling`
    
    -  `Azure VMSS` will not `decide` `how many VM` need to be `created` but the `Azure DevOps` decide `How Many VM instance` it need to run as the `Scaling type is as manual`
    
    - `Azure Devops` will send a request `Azure VMSS` `how many instance it need in order to run the pipeline`  
    
    - even though the `instial instance count` been set to `2` but from `Azxure Devops` we can scale down to `0 instance`

- **How to Link the Azure VMSS with Azure DevOps**
  
  - go to the `dev.azure.com` which is for the `Azure DevOps` &rarr; `Project Setting` &rarr; `Agent Pool` &rarr; `Add Pool` &rarr; `select the New Pool to Link` &rarr; `Select the pool type as Azure VMSS( which can be self hosted agent or Azure VMSS)`  &rarr; `select Azure VMSS` &rarr; `select the Azure Subscription` &rarr; `Azure VMSS that we have created` &rarr; `select Name for the Azure VMSS` &rarr; `select the pool option`  such as 
    
    - `Autiomatic Teardown Virtual Machine in scale set` as `Ticked`
    
    - `Mximum Number of Virtual Machine in the Scale set` as `5` 
    
    - `Number of Agent to keep on standby` as `0` 
    
    -  `Deplay in minute before deleting excess idle agent` as `0`
    
    - `Grant All Permission to the Pipeline`

  - now the `Azure Devops` connecting to the `Azure VMSS` using the `Azure Subscription`
  
  - we can see the `name of the Azure VMSS` that we have provided in here 
  
  - we can go to the `settings` to see the `pool option` that we have selected
  
  - in the `agent` section we should see the `Azure VMSS VM` , but by default it will not be shown 
  
  - for the `Azure VMSS VM` to be listed inside the `agent` we need to `update the Azure VMSS VM`
  
  - go to `Azure Portal` using the `portal.azure.com` &rarr; `select the Azure VMSS` &rarr; `select the VM` &rarr; `select both the VM` &rarr; `click on upgrade`
  
  - once upgraded the `Agent section of Azure Devops` we can see the `Azure VMSS Instance VM`
  

- **How to Use the `Azure VMSS VM as Build Agent` inside the Azure CICD pipeline**

  - when we use the `Microsoft Hosted Build agent` typically we select the `vmImage` we want to run 
  
  - but in this case we need to select the `name of the Azure VMSS we provided in Azure Devops` against the `name` declarative of the `Azure DevOps Pipeline` pool section
  
  - we now then run the pipeline as below 
    
    ```yaml
        azure-pipelines.yaml
        ====================
        trigger:
            - master
        
        pool:
          name: 'myvmssagent'
        
        jobs:
        
        - job: Job1
          steps:
            - script: echo Hello, $HOSTNAME
        
        - job: Job2
          steps:
            - script: echo Hello, $HOSTNAME
        
        - job: Job3
          steps:
            - script: echo Hello, $HOSTNAME
        
        - job: Job4
          steps:
            - script: echo Hello, $HOSTNAME
        

    ```





 
