# Anatomy Of Azure ARM Template


- here we will learning the `Basics of an ARM template`

- we will be looking at 
  
  - `How to create a ARM Template` and `How that look like`
  
  - `What Language the ARM Template Use`
  
  - `How to Create the Resources using the ARM template`
  
  - we will be deploying the `very first resources` using the `Azure ARM template` 


- `Azure ARM template` were `written` in `JSON` `language`

- we can `write` as `arm!` which will provide the `Boilerplate/sceleton of a Azure ARM template` with all the `section` we need created 

- when we write the `arm!` then it will change the `JSON` into the `Azure ARM template` on the `bottom of the VSCode Screen` , which will `allow all the arm extension` on the `VScode`

- an `sceleton of the Azure ARM template` is just a `JSON object`

- a `Boilerplated ARM template` has `few section` such as 
  
  - `$Schema`

  - `contentVersion`  

  - `Parameters`

  - `Variables`
  
  - `resources`
  
  - `outputs`
  
  - `functions`   

- we might not have to use `All the section` , few of the `section` are `optional in nature`

- `$schema`
  
  - `ARM template` is a `Schemaful Language` , the `schema defined` for `How the ARM template` will be `described`
  
  - here the `extension` will provide the `date on which schema been created` with the `version`
  
- `contentVersion`
  
  - always the `contentVersion` being set to `1.0.0.0` 

- `parameters`
  
  - define `what value we can pass into` the `ARM template` when we want to `deploy the template` to `populate value` in the `file`
  
  - if we want to allow the `user of our ARM template` to pass `name/sizes/region` etc then we can `define` that as `parameter` and that can be passed during the `deployment time` and will be `replace or Substitute the value` in the `ARM template file values`
  
- `variables`
  
  - variables are `similar like paramters` , but we can't pass `variable outside from the Azure ARM template`
  
  - `variables` are `constants/ globals` defined in the `ARM template File`  
  
  - we have to define the `variables` in the `variables section` and use it inside the `templates`
  
  - if a value been used `multiple times` then we can set that `value` as the `variable` and we can change the `variable` and `corresponding value` will be changed 
  
  - this will be very useful while we are using the `function section` which we will discuss later 


- `resources`
  
  - here we need to `define` the `actual thing we want to deploy` into the `Azure`
  
  - `every item resources` such as below considered as `resource` as the `Azure ARM template concerned`
    
    - `storage account`
    
    - `virtual machine `
    
    - `SQL Database ` 
  
- `outputs`
  
  - the `Azure ARM template` can `output info` as the `ARM tmplate being run`
  
  - we can define the `output info` which need to be `displayed` which can be from `other parts of the template` such as `variable` or `resource URL`
  
  -  for example
     
     - if we are creating the `storage account` we can output the `URL of that Storage account`
     
     - we can output the `variables` or `parameters provided by the user` 
     
     - we can `output` the `info values` into the `view it in the command line`
     
     - if we are using the `nested ARM template` then we can output a `value` from `one template to another template`
     
- `functions`
  
  - this is a `newish section`  
  
  - this allow us to define `custom function` inside the `ARM template`
  
  - for now we will not be using it , once we look into the `user defined function` we can use the same for reference 
  
  - if we are not using then we can `renmove` the `function` section in here 


- **creating the Azure Resource using the ARM template**
  
  - here we will be creating a `storage account` in `Azure Resources` as it need `few option to be created`
  
  -  


