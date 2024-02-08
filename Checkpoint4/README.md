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

```
AllowForwardedTraffic    AllowGatewayTransit    AllowVirtualNetworkAccess    DoNotVerifyRemoteGateways    Name            PeeringState    PeeringSyncLevel    ProvisioningState    ResourceGroup       ResourceGuid                          UseRemoteGateways
-----------------------  ---------------------  ---------------------------  ---------------------------  --------------  --------------  ------------------  -------------------  ------------------  ------------------------------------  -------------------
True                     False                  True                         False                        ServertoRouter  Connected       FullyInSync         Succeeded            Student-RG-1202207  75d3058a-8274-0242-32d2-66afbd3d7835  False

```

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

```
AddressPrefix    HasBgpOverride    Name              NextHopIpAddress    NextHopType       ProvisioningState    ResourceGroup
---------------  ----------------  ----------------  ------------------  ----------------  -------------------  ------------------
172.17.88.32/27  False             Route-to-Server   192.168.88.36       VirtualAppliance  Succeeded            Student-RG-1202207
10.13.175.0/24   False             Route-to-Desktop  192.168.88.36       VirtualAppliance  Succeeded            Student-RG-1202207

```

6. Get the details of route between your `Router-xx SN1` and `Server-xx SN` using `az network route-table route show` and send the output in `json` format to `route_details.json`

      [route_details.json](./route_details.json)


7. (Optional) What CLI command will show you which subnet is associated to which route in route table? _(Hint: maybe start with 'az network vnet subnet show`)_

`az network route-table route list`


### [Part C - Network Review Questions](#header3)

1. What is Azure Virtual Network (VNET)? Elaborate in your own words, you may use diagrams if drawn by yourself.
    - The Azure Virtual Network (VNET) is basically a space allocated in the Azure cloud platform where you can setup different resources depending on what a user needs when doing any infrastructure building in the internet. This can range from making virtual machines, apps, subnets, security groups and more.  
    ![vnet-diagram](VNET-diagram.png)
2. In the context of Hybrid Cloud architecture. How on-prem computers can access resources inside Azure virtual network?
    - An on-prem network of computers in a Hybrid Cloud architecture can access resources inside an Azure virtual network is though an Azure Virtual Network Gateway (VPN) which are done usually in two methods, Site-to-Site, which involves setting up a VPN connection between the on-prem network and the Azure VNET, and a ExpressRoute which is almost the same thing as a Site-to-Site but is for higher performance and a more dedicated connection through private means.
3. What are the most important benefits of Azure Virtual Networks? Elaborate in your own words. Do not copy/paste from Azure Documentation. Itemized list of just benefit without proper elaboration will not receive any marks
    - Environment isolation for applicaitons - this allows users to create unique and organized environments for different applications or organizational units.
    - Subnetting feature - This helps organizations organize their inner network and databases in the company to keep things orderly and easy to manage.
    - Traffic direction - An Azure Virtual Network comes with Azure Load Balancer which is a service that can help distribute incoming network traffic across multiple VM's to ensure high availability on a users applications.
    - Secure network - Network Security gorups are provided by allowing users to define rules that control inbound and outbound traffice to and from resoruces within a virtual network.
    - Dynamic Scaling - Virtual Networks can dynamically scale to accomodate the growth demands of applications and/or services if needed.
4. What is the difference between Network Security Group (NSG) and Route-Tables?
    - An NSG is primarily used in controlling the inbound and outbound traffic in a network, VM and subnets that allows or denies traffic based on rules defined by a user. While a Route Table on the other hand is used to control the routing of network traffic within a network and determines the where the traffic should be directed to based on the IP address.
5. What is the difference between NSG and Firewalls?
    - An NSG is the service or feature in Azure that controls the inbound and outbound traffic of a network while a Firewall is tool used along with NSG as another layer of security in a network.
6. What is a _hob-and-spoke_ network topology and how be deployed in Azure Cloud?
    - It is a network topology design where there is a central "hub" network that is connected to multiple "spoke" networks. The hub serves as a central meeting point of all spokes and spokes are nodes connected to a hub but not directly connected to other spokes.
7. In working with Azure VNETs, do you need to define gateways for Azure to route traffic between subnets?
    - The need for defining gatewats are dependant on the business need required to commuinicate between subnets within the same VNET or with other VNETS. When communicating with subnets within the same VNET, we dont need to setup gateways but if we need to communicate with other VNETS then we would need a gateway to route traffice appropritately between subnets.
8. When do you need to configure and use Virtual Network Gateways?
    - We usually need to configure and use Virtual Network Gateways when we need to enable a secure connection between different networks and depending on the network architecture of the VNET. Using Virtual Network Gateways provide securre tunnels and encryptions needed for data to flow between different network environments.

### [Part D - Creating Virtual Machines](#header4)

1. List all VMs and send the output in `table` format to `vm_list.tbl` file. What command did you use?

    - The command used is `az vm list --out table > vm_list.tbl`

    ```tbl
    Name    ResourceGroup       Location       Zones
    ------  ------------------  -------------  -------
    LR-88   STUDENT-RG-1202207  canadacentral
    LS-88   STUDENT-RG-1202207  canadacentral
    WC-88   STUDENT-RG-1202207  canadacentral
    WS-88   STUDENT-RG-1202207  canadacentral
    ```

2. Get the details of your `WC-88` using `az show` command and send the output in `json` format to `WC-88-details.json` file. What command did you use?

    - The command used is `az vm show --name WC-88 --resource-group Student-RG-1202207 --out json > WC-88-details.json`

    [WC-88-details.json](./WC-88-details.json)


3. List all NSG using `az list` command and send the output in `table` format to `nsg_list.tbl`file. What command did you use?

    - The command used is `az network nsg list --out table > nsg_list.tbl`

    ```
    Location       Name       ProvisioningState    ResourceGroup       ResourceGuid
    -------------  ---------  -------------------  ------------------  ------------------------------------
    canadacentral  LR-NSG-88  Succeeded            Student-RG-1202207  674e06ca-8977-4744-afa0-64e1aabc7856
    canadacentral  LS-NSG-88  Succeeded            Student-RG-1202207  2bf0d40b-c9eb-4596-8802-ebb99a70c9f6
    canadacentral  WC-NSG-88  Succeeded            Student-RG-1202207  bc551180-4278-45ff-a027-48a53a190148
    canadacentral  WS-NSG-88  Succeeded            Student-RG-1202207  849f7b78-51fd-4671-a6a3-b9c32dbeaa9a
    ```
4. Provide screenshot of _auto shutdown configuration_ for `LS_XX`. Is there any command to show this? What is the time-zone? What should be the correct time settings considering the time zone differences?

    - The command to show the auto-shutdown-configuration is `az vm auto-shutdown -g Student-RG-1202207 -n LS-88 --time 0500`.
    - The auto-shutdown uses the UTC timezone.
    - The time setting we use is "0500" which will configure: 12:00 midnight EST
    ![auto-shutdown-config](auto-shutdown-screenshot.png)


5. Why `auto shutdown configuration` is not done in [vm_create](https://github.com/Azure-Project-Winter2024/Azure-Project-Scripts/blob/94d21ad5454163ae8e2ee331f8a41291fca6e155/CP4-Scripts/bash-scripts/vm_create.sh#L128) code? Why is it a separate scripts? Is it possible to configure auto shutdown at the same time you are creating the VM?
    - The `auto shutdown configuration` is done in the `vm_create.sh` script and is also in a separate script. It is also possible to configure the auto shutdown and VM creation code in the same script but the `auto shutdown configuration` script needs a wait time while the VM's are being created before it can be executed.



### [Part E - Creating Custom Images](#Header5)


### [Part F - Clean Up your Environment](#Header6)
