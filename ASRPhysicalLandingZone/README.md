# ASR for physical machines Landing Zone

This project is intended to get you started with a basic deployment of Azure prerequisites to use ASR with your physical machines. Feel free to modify this template given your own needs. Here is the architecture that we are going to deploy:

<img src=images/ASRPhysical-Architecture.jpg/>

The template called **template.json** is intended to deploy the following resources:
- Storage Account without Soft delete enabled as required for ASR
- Virtual Network where the VMs will land after replication: change address space as per your own needs
- Network Security Group attached to the VNET subnet (default). Currently it has RDP port opened for a specific public IP
- Recovery Services Vault that is going to be used as the primary vault for replication to happen


## Important documentation
Make sure to check the following documentation when planning on ASR for physical machines. The JSON template is intended to simplify steps 1 - 3

### ARCHITECTURE
https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-architecture

### REQUIREMENTS and STEPS
1. Deploy a Recovery Services Vault Prepare Azure for on-premises disaster recovery with https://docs.microsoft.com/en-us/azure/site-recovery/tutorial-prepare-azure#create-a-recovery-services-vault
2. Set up an Azure Network: where the VMs will land once failover is done: Prepare Azure for on-premises disaster recovery with https://docs.microsoft.com/en-us/azure/site-recovery/tutorial-prepare-azure#set-up-an-azure-network
3. Create a Storage Account that does not have Soft Delete enabled
4. Think and prepare how you will connect to the replicated VMs: https://docs.microsoft.com/en-us/azure/site-recovery/hyper-v-prepare-on-premises-tutorial#prepare-to-connect-to-azure-vms-after-failover
5. Prepare the servers for installing the Mobility service: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-disaster-recovery#set-up-an-azure-storage-account
6. Review you meet prerequisites for supported configuration: https://docs.microsoft.com/en-us/azure/site-recovery/vmware-physical-secondary-support-matrix
7. Setup Configuration and Process server: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-set-up-source
8. Create a replication policy: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-disaster-recovery#create-a-replication-policy
9. Enable Replication: https://docs.microsoft.com/en-us/azure/site-recovery/physical-azure-disaster-recovery#enable-replication
10. Test Failover: https://docs.microsoft.com/en-us/azure/site-recovery/tutorial-dr-drill-azure



