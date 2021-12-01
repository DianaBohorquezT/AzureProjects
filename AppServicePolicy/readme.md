# How to deploy and assign policies

This document is intended to explain how to deploy Azure policy LimitSKUAppService.json to Azure.

There are three main concepts about policies on Azure that need to be clear in order to use them correctly for your resources:

 ## Policy Definition
 A policy definition contains the code for a single policy. It can be either Built-in (provided by Azure) or Custom, like the ones we are creating here. You can create a policy definition by following the steps on this documentation, it includes both Azure Portal and CLI/API/PowerShell deployment: 

https://docs.microsoft.com/en-us/azure/governance/policy/tutorials/create-and-manage#implement-a-new-custom-policy


## Policy Initiative Definition

A group that contains several policy definitions. You can assign multiple policies or instances of a single policy to a policy initiative. Here is more information:

https://docs.microsoft.com/en-us/azure/governance/policy/tutorials/create-and-manage#create-and-assign-an-initiative-definition

## Policy Assignment

Create a new assignment of the policy to choose which resources will be enforced to use the policy: you can choose either the whole subscription or a specific resource group. You can choose to assign individual policies or policy initiative definitions depending on your needs. Refer to this documentation as well to create a policy assignment:

https://docs.microsoft.com/en-us/azure/governance/policy/tutorials/create-and-manage#create-and-assign-an-initiative-definition


Once the policy is assigned to the desired scope be patient! It might take up to 30 minutes for it to apply. Once applied, you can verify the compliance of your resources. Here you can find more information on how compliance is evaluated:

https://docs.microsoft.com/en-us/azure/governance/policy/how-to/get-compliance-data

# Suggested steps to test these policies

This is a series of steps that I suggest for you to test these policies:

1. Create the Policy Definition on your subscription using the file LimitSKUAppService.json
2. Create a policy assignment and choose the scope where you want the policy to apply. On Parameters tab choose if you want to Audit or Deny the assignment.
3. Once the policy is assigned, test creating the SKU types that you have allowed and the ones you have denied: you should get a policy error for the not allowed SKUS. Remember replication might take time so make sure to wait a couple of minutes after assignment before testing this

