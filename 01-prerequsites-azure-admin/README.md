# Prerequisites: Azure Resource Manager (ARM) Templates

## Goal
The goal of these exercises was to understand how to define, deploy, and improve Azure infrastructure using ARM templates.

Two key exercises were completed:

- Create and deploy an ARM template  
- Add parameters and outputs to an ARM template  

These exercises introduced the foundation of Infrastructure as Code (IaC) in Azure.

---

## What Was Built
A basic ARM template was created and deployed to Azure to provision resources declaratively. The template was then enhanced by introducing parameters for flexibility and outputs for visibility after deployment.

---

## Exercise 1: Create and Deploy ARM Template

In this exercise, I created and deployed my first ARM template using Visual Studio Code and Azure PowerShell instead of using the Azure portal.

I started by creating a JSON template file that defines an Azure storage account. The template included the required schema, content version, and a `resources` section where the storage account was defined.

For this deployment, I used:
- **Resource group:** `rg-arm-lab`  
- **Location:** `canadacentral`  
- **Storage account:** `addresource`  

Instead of manually creating the storage account through the portal, everything was defined in the template and deployed through PowerShell. This showed how Azure can take a JSON file and provision resources exactly as described.

After deployment, I verified the results in the Azure portal:
- The resource group `rg-arm-lab` contained the storage account `addresource`
- The deployment showed as **Succeeded** under the deployments tab
- The storage account was created with the expected configuration (StorageV2, Standard LRS, Canada Central)

### Screenshots

Screenshots for proof of work can be found within the screenshots folder and are as follows:

- Resource group with deployed resource   
- Successful deployment in Deployments tab  
- Storage account overview  

This exercise showed how ARM templates remove manual steps and allow consistent, repeatable deployments using code.

---

## Exercise 2: Add Parameters and Outputs to ARM Template

In this exercise, I updated the existing ARM template to make it more flexible and reusable by introducing parameters and outputs.

Instead of hardcoding values in the template, I added parameters for:
- `storageName`
- `storageSKU`

This allowed me to pass values at deployment time rather than editing the template for every change. I also defined allowed values for the SKU and set a default to `Standard_LRS`.

For this deployment, I used:
- **Resource group:** `rg-arm-lab`  
- **Storage account:** `parameterstoragemustafa2`  
- **SKU:** `Standard_LRS`  

The deployment was executed using PowerShell by passing in the parameter values directly:

```powershell
New-AzResourceGroupDeployment -Name $deploymentName -TemplateFile $templateFile -storageName parameterstoragemustafa2 -storageSKU Standard_LRS
```
I also added an outputs section to the template to return useful information after deployment. In this case, I returned the storage account’s primary endpoints using:

```
"[reference(parameters('storageName')).primaryEndpoints]"
```
After deployment, I verified:

- The deployment completed successfully  
- The storage account `parameterstoragemustafa2` was created in `rg-arm-lab`  
- The outputs section returned the storage endpoints (blob, queue, table, file, etc.)  

This showed how templates can not only deploy resources, but also return useful data for validation or further use.

### Screenshots

Screenshots for proof of work can be found within the screenshots folder and are as follows:

- ARM template in VS Code showing parameters and outputs  
- PowerShell deployment command with parameters  
- Successful deployment in Deployments tab  
- Outputs tab showing returned storage endpoints  
- Storage account overview  

This exercise showed how parameters make templates reusable and how outputs provide visibility into deployed resources.

---

## Conclusion

These exercises established a strong foundation in working with ARM templates.

Key takeaways:

- Azure resources can be fully defined and deployed using code  
- ARM templates enable consistent and repeatable deployments  
- Parameters make templates reusable across different environments  
- Outputs provide visibility into deployed resources  

This is a fundamental skill for managing Azure environments at scale and will be built upon in later modules.

See the [Create, configure, and manage identites documentation](../02-create-configure-manage-identities/README.md) for the next exercises.