# CAA-900-AzureProject

# Checkpoint5 Submission

- **COURSE INFORMATION: CAA900ZAA**
- **STUDENT’S NAME: Isaiah Cyrus Majam**
- **STUDENT'S NUMBER: 129325239**
- **GITHUB USER_ID: 129325239-mysenecaa**
- **TEACHER’S NAME: Atoosa Nasiri**

## Table of Contents

1. [Part A - Creating & Configuring VMs - Using Portal](#header)
2. [Part C - Enable IP_Forwarding - Using Portal](#header)
3. [Part B - Basic Connectivity - VM Configuration](#header)
4. [Part D - Creating & Configuring VM Images - Using Portal](#header)
5. [Part E - Azure Cost Analysis Charts](#header)
6. [Part F - Create Customized Azure Dashboard](#header)

### [Part A - Creating & Configuring VMs - Using Portal](#header)

1. What is the difference between Windows machine NSG and Linux machine NSG rules? Why? **Do not give screenshots** just describe the difference? Do you need a rule for `ssh` or `rdp`? What happens if you delete specific `ssh` and `rdp` rules?
    <p>&nbsp;&nbsp;
    The difference between the Windows and Linux machine NSGs are the ports they are associated with. For Windows NSG, it is the RDP port which is port 3389 and for Linux NSG it is the SSH port which is port 22. This is done as a standard best practice when doing NSG configurations so that no unnecessary open ports will be used maliciously or incorrectly which helps in controlling and restricting traffic depending on the need.

    &nbsp;&nbsp;We need the rules for `ssh` and `rdp` because we would need to allow inbound traffic to the SSH port 22 or to RDP to port 3389 to enable secure access to the machines and/or to remotely manage machines depending on the need. 

    &nbsp;&nbsp;When we delete `ssh` and `rdp` rules we wont be able to establish SSH and RDP connections to Linux and Windows machines respectively.
    </p>
2. Work from Azure Bash CLI in **Portal** to get a list of your VM, NSG, NIC, and Disks. You can start with the below commands. Make sure the outputs in table format are embedded in your submission.

    `az group list -out table`

    ```bash
    Name                Location       Status   
    ------------------  -------------  ---------
    Bastion_RG          canadacentral  Succeeded
    NetworkWatcherRG    canadacentral  Succeeded
    Student-RG-1202207  canadacentral  Succeeded
    ```

    * create a variable with your student resource group to make your job easier! <br />
    `RG="Student-RG-1202207"`

    * get a list of your VM, NSG, NIC, Disks <br />
    `az vm list -g $RG -o table`

    ```bash
    Name    ResourceGroup       Location       Zones
    ------  ------------------  -------------  -------
    LR-88   Student-RG-1202207  canadacentral  1
    LS-88   Student-RG-1202207  canadacentral  1
    WC-88   Student-RG-1202207  canadacentral  1
    WS-88   Student-RG-1202207  canadacentral  1
    ```


    `az network nic list -g $RG -o table`

    ```bash
    AuxiliaryMode    AuxiliarySku    DisableTcpStateTracking    EnableAcceleratedNetworking    EnableIPForwarding    Location       MacAddress         Name         NicType    Primary    ProvisioningState    ResourceGroup       ResourceGuid                          VnetEncryptionSupported
    ---------------  --------------  -------------------------  -----------------------------  --------------------  -------------  -----------------  -----------  ---------  ---------  -------------------  ------------------  ------------------------------------  -------------------------
    None             None            False                      False                          False                 canadacentral  00-0D-3A-E8-43-83  lr-88439_z1  Standard   True       Succeeded            Student-RG-1202207  8247b324-92eb-4075-8046-d353134fd748  False
    None             None            False                      False                          False                 canadacentral  60-45-BD-5C-59-DE  ls-88829_z1  Standard   True       Succeeded            Student-RG-1202207  4685cc5b-61a3-4ddb-b1ba-94d683e81760  False
    None             None            False                      False                          False                 canadacentral  00-22-48-B0-F9-3E  wc-88791_z1  Standard   True       Succeeded            Student-RG-1202207  1ac50127-64ba-4601-acf1-c346453b1745  False
    None             None            False                      False                          False                 canadacentral  00-22-48-AD-8F-F0  ws-88796_z1  Standard   True       Succeeded            Student-RG-1202207  c2dac78c-dca3-48b5-8e30-0ac6a9d8ff5b  False
    ```


    `az network nsg list -g $RG -o table`

    ```bash
    Location       Name       ProvisioningState    ResourceGroup       ResourceGuid
    -------------  ---------  -------------------  ------------------  ------------------------------------
    canadacentral  LS-88-nsg  Succeeded            Student-RG-1202207  61284cc6-4262-434e-96bc-d66302fba3f3
    canadacentral  WC-88-nsg  Succeeded            Student-RG-1202207  ee1785e1-943e-40f9-a88c-4d5c9aa83eb3
    canadacentral  WS-88-nsg  Succeeded            Student-RG-1202207  511e502d-dfde-46e4-bfe3-768c35b50d79    
    ```


    `az disk list -g $RG -o table`
    
    ```bash
    Name                                             ResourceGroup       Location       Zones    Sku           OsType    SizeGb    ProvisioningState
    -----------------------------------------------  ------------------  -------------  -------  ------------  --------  --------  -------------------
    LR-88_OsDisk_1_6a3252da362e4215ba2ae64359d7cbbf  Student-RG-1202207  canadacentral  1        Standard_LRS  Linux     64        Succeeded
    LS-88_OsDisk_1_dd872ca37b5b4c10bdc39aac055f800d  Student-RG-1202207  canadacentral  1        Standard_LRS  Linux     64        Succeeded
    WC-88_OsDisk_1_8301563364674ee9a4058acc447a3efa  Student-RG-1202207  canadacentral  1        Standard_LRS  Windows   127       Succeeded
    WS-88_OsDisk_1_4213db92346e4cbe84108f377f376196  Student-RG-1202207  canadacentral  1        Standard_LRS  Windows   127       Succeeded
    ```


### [Part C - Enable IP_Forwarding - Using Portal](#header)

### [Part B - Basic Connectivity - VM Configuration](#header)

### [Part D - Creating & Configuring VM Images - Using Portal](#header)

### [Part E - Azure Cost Analysis Charts](#header)

### [Part F - Create Customized Azure Dashboard](#header)