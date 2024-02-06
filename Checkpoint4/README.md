# CAA-900-AzureProject


# Checkpoint4 Submission

- **COURSE INFORMATION: CAA900ZAA**
- **STUDENT’S NAME: Isaiah Cyrus Majam**
- **STUDENT'S NUMBER: 129325239**
- **GITHUB USER_ID: 129325239-mysenecaa**
- **TEACHER’S NAME: Atoosa Nasiri**


## Table of Contents

1. [Part A - Creating Network Resources using Azure CLI](#header1)
2. [Part B - Working with Azure CLI Bash](#header2)
3. [Part C - Network Review Questions](#header3)
4. [Part D - Creating Virtual Machines](#header4)
5. [Part E - Creating Custom Images](#Header5)
6. [Part F - Clean Up your Environment](#Header6)

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


### [Part B - Working with Azure CLI Bash](#header2)

1. List all VNETs using `az network vnet list` command and send the output in `json` format to `vnet_list.json`file

[vnet_list.json](./vnet_list.json)

2. Get the details of your `default student vnet` using `az show` command and send the output in `json` format to `student_vnet.json` file  

[student_vnet.json](./student_vnet.json)

3. List all peerings using `az network vnet peering list` command and send the output in `table` format to `peerings.tbl`file

[peerings.tbl](./peerings.tbl)

4. Get the details of your `Router-XX` subnet `SN1` using `az show` command in `json` format and `query` it for details of subnet and rout associations. Only submit 
the specific property you are asked for. You will need to embed this in your `README.md` as per instructions.

```json
{
  "AddressPrefix": "192.168.88.32/27",
  "Associations": null,
  "Subnet": "SN1"
}
```

5. List all routes in `RT-xx` using `az network route-table route list` command and send the output in `table` format to `route_list.tbl`file

[route_list.tbl](./route_list.tbl)

6. Get the details of route between your `Router-xx SN1` and `Server-xx SN` using `az network route-table route show` and send the output in `json` format to `route_details.json`

[route_details.json](./route_details.json)

7. (Optional) What CLI command will show you which subnet is associated to which route in route table? _(Hint: maybe start with 'az network vnet subnet show`)_

`az network route-table route list`


### [Part C - Network Review Questions](#header3)



### [Part D - Creating Virtual Machines](#header4)


### [Part E - Creating Custom Images](#Header5)


### [Part F - Clean Up your Environment](#Header6)
