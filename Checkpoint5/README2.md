## ✨ Part B - Enable IP_Forwarding - Using Portal

1. Check the status of ip-forwarding using the command `az network nic ip-config show` with output format as `json`. Include **only** the command **not output** including the `--quey` you used in your submission.
2. When your output format is `json`, which property shows the status of the ip-forwarding attribute? Embed **only** the property that shows the status of ip-forwarding.
3. Check if the IP forwarding in NIC is enabled using Azure bash. 👉 Hint: `az network nic show -g <rg-name> -n <nic-name> --query "enableIpForwarding"`


## ✨ Part C - Basic Connectivity - VM Configuration

1. In configuring your Linux VMs, for the step "Remove the `firewalld` service", which command will you be using?
2. In configuring your Linux VMs, what command do you use to check the status of `iptabels`?
3. How can you make iptables service start automatically after reboot on CenOS/RHEL8? 👉 Hint: [RHEL7: How to disable `Firewalld`` and use Iptables instead](https://www.certdepot.net/rhel7-disable-firewalld-use-iptables/)
4. Run a command in `LR-xx` that shows all `iptables` chains with their order number. What is the default setting? Include both the command and its output in your submission. How could you improve these settings to be less vulnerable to attacks?
5. Run a command that shows the hostname in `LR-XX` and `LX-XX`. Embed the output in your submission.


## ✨ Part D - Creating & Configuring VM Images - Using Portal

1. Run a command in CLI that lists all your Custom Images. Hint: `az image list ...`. Change the output format to table format and embed the answer in your submission.
2. Delete your VMs after your work is completed. Run a command in CLI that lists all your VMs. Hint: `az vm list ...`. Change the output format to table format and embed the answer in your submission.
3. Recreate all VMs from your images, and establish basic connectivity. How long the entire process took? How can you do this more efficiently?

## ✨ Part E - Azure Cost Analysis Charts

1. Follow the instructions and create a Cost Analysis table similar to the sample given to you and embed it in your submission. **Do not put it in a separate file, add it to your README.md, but you can keep images in a separate folder. It makes your folder clean and more accessible**

## ✨ Part F - Create Customized Azure Dashboard

1. Follow the instructions and create a customized Dashboard that contains the minimum above resources in a configuration similar to the sample given to you and embed it in your submission. **Do not put it in a separate file, add it to your README.md, but you can keep images in a separate folder. It makes your folder clean and more accessible**
