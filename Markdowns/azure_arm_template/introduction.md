# Introduction to Azure ARM Template


- **What Are ARM Template**
  
  - `Azure Resource Manager` is the `underlying fabric` that `control` the `deployment of resources in Azure Works`
  
  - `preveiously` it is called as the `Azure Service Manager` using which `Old vm` and `cloud services` are being `deployed` , which is `deprecated` and `replaced` by the `Azure Resource Manager`
  
  - `Azure ARM` is the `new way to manage` your `deployment` and look after the `infrastructure running in azure`
  
  - using the `Azure ARM` we can define `How to define the infrastructure to deploy` and `also deploy the same`
  
  - `Azure ARM` is the `microsoft way of using the Infrastructure as Code (IaaC)`
  
  - `IaaC` `is a techinque` to `define the infrastructure in the code file` rather than `going to do it manually`
  
  - the `big difference` between the `Azure ARM template` and `Powershell script` being `Azure ARM` is `declarative` not `imparative` like `Powershell`
  
  - when we write the `Poershell Script` we are instructing it to run `multiple commands` to `do this and this and this`
  
  - but with the `Azure ARM template` we are not doing that , here we are `declaring` the `infrastructure` where we will be saying as 
    
    - my infrastructure should consist of a 
      
      - `storage account`
      
      - `SQL Database`
      
    - we are also providing the `params`  to `define that infrastructure`  such as 
      
      - `the region` 
      
      - `the Size `  
    
    - here we are not `intersted` , how these `resources` are `deployed under the hood`  that the `job of the ARM Fabrics`
    
    - the `Azure Platform` will take care of `interpreting the same declarative infrastructure` and `turning them into the actual infrastructure`
    
    - `Azure ARM templates` were `idempotent in nature` , hence we can `run` the `template` as `Many time as we want` , we will be getting the `same result` each time
    
    - we can use the `same Azure ARM template to` deploy `multiple different environment` using the same `declarative syntax` and changing the `parameters` , we will be getting the `same environment back` except `the paramters that we have used` but the `result of the Azure ARM template` will be same 
    
    - different `IaaC` tools are of 
      
      - Azure has the `ARM template`
      
      - AWS has `cloud Formation` as `IaaC`
      
      - some of them are `multi platform  or on premises support` such as `Terraform or Pulumi`
      
    - we will be using the `Azure ARM template` to `deploy infrastructure to Azure Cloud`


- **Pre-Requisite and SetUp for the Azure ARM Template**
  
  -  
