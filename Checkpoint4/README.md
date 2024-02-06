# CAA-900-AzureProject


# Checkpoint4 Submission

- **COURSE INFORMATION: CAA900ZAA**
- **STUDENT’S NAME: Is  aiah Cyrus Majam**
- **STUDENT'S NUMBER: 129325239**
- **GITHUB USER_ID: 129325239-mysenecaa**
- **TEACHER’S NAME: Atoosa Nasiri**


## Table of Contents
1. [Part A - Creating Network Resources using Azure CLI](#Part-A---Manage-Conflicts---Overwrite-Remote-Changes)
2. [Part B - Manage Conflicts - Reset Local Commit Head](#Part-B---Manage-Conflicts---Reset-Local-Commit-Head)
3. [Part C - Manage Conflicts - Merge Editor](#Part-C---Manage-Conflicts---Merg-Editor)
4. [Part D - Collaboration - Creating Pull Request](#Part-D---Collaboration---Creating-Pull-Request)


### Part A - Creating Network Resources using Azure CLI

```
# //////////////////////////////////////////////////////////////
# Update the lines that are specific to your network 
# /////////////////////////////////////////////////////////////

RG_NAME="Student-RG-1202207"     # your student group
LOCATION="canadacentral"    # your location
ID="88"          #unique ID assigned to you

Student_vnet_name="Student-1202207-vnet"
Student_vnet_address="10.13.175.0/24"
Client_Subnet_name="Virtual-Desktop-Client"
Client_Subnet_address="10.13.175.0/24"
```

Answer below questions:

- In network_config_test.sh what does if [[ ! $(az group list -o tsv --query "[?name=='$RG_NAME']") ]] do? Explain your answer.

-- This command will check the list of resources in the Azure accounts Resource groups and checks if it is equal to resource name from the network_config.sh    

- Why is it crucial to check if a resource exist before creating it? What bash syntax do you use to test this? How do you check if a vnet exists in vnet_create.sh?

-- It is better to check if a resource is existing before creating it so that it would not be a waste of resources when they could just be re-used and modified which can result into loss of data, unnecassry consumption, and conflicting operations. To check if a vnet exists in the vnet_create.sh it is used in the following syntax:
`if [[ $(az network vnet list -g $RG_NAME -o tsv --query "[?name=='$vnet']") ]]`

- What is the Azure CLI command to create vnet? Give the specific command as per your environment and unique ID configuration. What are the required and what are the optional parameters that you need to pass to it?

Azure CLI Command:
`az network vnet create`    
Specific Command per my environment and unique ID configuration:

```bash
az network vnet create -g $RG_NAME \
            --name $vnet \
            --location $LOCATION \
            --address-prefix $address_prefix
```

Required Parameters:

```bash
--name
--resource-group
```

Optional Parameters:
```bash
--address-prefixes
--subnet-name
--subnet-prefix
--location
--dns-servers
--ddos-protection-plan
--vm-protection-enabled
--vm-protection-mappings
```

- What is the Azure CLI command to create subnet? Give the specific command as per your environment and unique ID configuration.    

Azure CLI Command:
`az network vnet subnet create`

Specific Command per my environment and unique ID configuration:
```bash
az network vnet subnet create --name $subnet_name \
                        -g $RG_NAME \
                        --vnet-name $vnet \
                        --address-prefix $address_prefix
```

Required Parameters:

```bash
--name
--vnet-name
--resource-group
```

Optional Parameters:
```bash
--address-prefix
--network-security-group
--route-table
--delegations
--service-endpoints
--private-endpoint-network-policies
--disable-private-link-service-network-policies
--nat-gateway
--disable-dns-registration
```