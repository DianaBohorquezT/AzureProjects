# ASR for physical machines Landing Zone

This project is intended to get you started with a basic deployment of Azure prerequisites to use ASR with your physical machines. Feel free to modify this template given your own needs. Here is the architecture that we are going to deploy:

<img src=images/ASRPhysical-Architecture.jpg/>

The template called [template.json](template.json) is intended to deploy the following resources:
- Storage Account without Soft delete enabled as required for ASR
- Virtual Network where the VMs will land after replication: change address space as per your own needs
- Network Security Group attached to the VNET subnet (default). Currently it has RDP port opened for a specific public IP
- Recovery Services Vault that is going to be used as the primary vault for replication to happen

You can use [parameters.json](parameters.json) to enter custom values to the parameters stablished on the template.json file.

## Target audience

- Infrastructure Architect
- IT Professional
- Cloud Solution Architect

## Important documentation
Make sure to check the following documentation when planning on ASR for physical machines. The JSON template is intended to simplify steps 1 - 3

### ARCHITECTURE
https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-architecture

### REQUIREMENTS and STEPS
1. Deploy a Recovery Services Vault Prepare Azure for on-premises disaster recovery with https://docs.microsoft.com/en-us/azure/site-recovery/tutorial-prepare-azure#create-a-recovery-services-vault
2. Set up an Azure Network: where the VMs will land once failover is done: Prepare Azure for on-premises disaster recovery with https://docs.microsoft.com/en-us/azure/site-recovery/tutorial-prepare-azure#set-up-an-azure-network
3. Create a Storage Account that does not have Soft Delete enabled
4. Think and prepare how you will connect to the replicated VMs: https://docs.microsoft.com/en-us/azure/site-recovery/hyper-v-prepare-on-premises-tutorial#prepare-to-connect-to-azure-vms-after-failover
5. Prepare the servers for installing the Mobility service: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-disaster-recovery#set-up-an-azure-storage-account. Make sure you read the Mobility Service documentation as well: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-physical-mobility-service-overview
6. Review you meet prerequisites for supported configuration: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-physical-secondary-support-matrix
7. Setup Configuration and Process server: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-set-up-source
8. Create a replication policy: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-disaster-recovery#create-a-replication-policy
9. Enable Replication: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-disaster-recovery#enable-replication
10. Test Failover: https://docs.microsoft.com/en-us/azure/site-recovery/tutorial-dr-drill-azure

### To failback on VMWare VMs
Physical servers replicated to Azure using Site Recovery can only fail back as VMware VMs. You need a VMware infrastructure in order to fail back. The infrastructure is also more complex and can be found in this doc https://docs.microsoft.com/en-us/azure/site-recovery/vmware-azure-prepare-failback

Follow the next steps to deploy the needed environment and test.

1. Read the general info about failback: https://docs.microsoft.com/en-us/azure/site-recovery/physical-to-azure-failover-failback
2. Prepare for reprotection/failback: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-azure-prepare-failback
3. Set up failback process server in Azure: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-azure-set-up-process-server-azure
4. Set up the Linux master target server in case the machines you are going to failback are Linux: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-azure-install-linux-master-target
5. Reprotect from Azure to on-premise: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-azure-reprotect
6. Failback to OnPremises: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-azure-failback

## Deploying an ARM Template using the Azure portal

- Visit https://portal.azure.com
- On the Search Bar, search for **Templates** 
<img src=images/Search.png/>
- Create a new template 
<img src=images/create.png/>
- Give it a name and a description 
<img src=images/name_desc.PNG/ width="700">
- On ARM template tab, copy and paste the code of the [template.json](template.json) and save it 
<img src=images/add_code.png/ width="700">
- Select the newly added template and click deploy 
<img src=images/deploy.png/ width="700">
- Fill out the blanks with your details and click purchase 
<img src=images/Fill_out_details.png/ width="700">
- On a few minutes, the deployment should be ready to use.

