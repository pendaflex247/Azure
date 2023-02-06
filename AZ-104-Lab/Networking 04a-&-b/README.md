
# Objectives
In this lab, you will:

    Task 1: Create and configure a virtual network
    Task 2: Deploy virtual machines into the virtual network
    Task 3: Configure private and public IP addresses of Azure VMs
    Task 4: Configure network security groups
    Task 5: Configure Azure DNS for internal name resolution
    Task 6: Configure Azure DNS for external name resolution

# Network Map

![](Image/az104lab04.png)
<img src="Image/az104lab04.png" width="900" >

# Task 1: Create and configure a virtual network with two subnets

Create a resource group
-

![](Image/a-6104lab04_11_55.png)

<img src="Image/a-6104lab04_11_55.png" width="900" >

![](Image/a-6104lab04_11_56.png)

![](Image/a-6104lab04_12_03.png)

Create a virtual network
-

![](Image/a-6urelab-04_12_06.png)

![](Image/a-6urelab-04_12_14.png)

![](Image/a-6urelab-04_12_22.png)

![](Image/a-6urelab-04_12_23.png)


Create two subnets
-

    -ipadd space 10.40.0.0/20
    -subnet0 10.40.0.0/24
    -subnet1 10.40.1.0/24


![](Image/a-6urelab-04_12_37.png)

![](Image/a-6urelab-04_12_38.png)

![](Image/a-6urelab-04_12_39.png)

<img src="Image/a-6urelab-04_12_39.png" width="1000" >

Create Virtual machine in both subnets using ARM
-

![](Image/a-6urelab-04_02_18.png)

![](Image/a-6urelab-04_02_20.png)


-Upload the templates

![](Image/a-6urelab-04_02_45.png)

# TASK 2: Deploy two virtual machines using the template and paramenter files on powershell

    $rgName = 'az104-04-rg1'

    New-AzResourceGroupDeployment `
        -ResourceGroupName $rgName `
        -TemplateFile $HOME/az104-04-vms-loop-template.json `
        -TemplateParameterFile $HOME/az104-04-vms-loop-parameters.json

![](Image/a-6urelab-04_02_48.png)

![](Image/a-6urelab-04_02_50.png)

![](Image/a-6urelab-04_02_52.png)

-verify the vm were created

![](Image/a-6urelab-04_02_56.png)


# TASK 3: Configure private and public IP addresses of Azure VMs

![](Image/a-6urelab-04_06_00.png)

![](Image/a-6urelab-04_06_01.png)

![](Image/a-6urelab-04_06_06.png)

![](Image/a-6urelab-04_06_07.png)

![](Image/a-6urelab-04_06_01.png)

![](Image/a-6urelab-04_06_17.png)

![](Image/a-6urelab-04_06_18.png)

![](Image/a-6urelab-04_09_58.png)

![](Image/a-6urelab-04_09_59.png)


# TASK 4: Configure network security groups  
-In order to allow for restricted connectivity to Azure virtual machines.


![](Image/a-6urelab-04_10_09.png)

![](Image/a-6urelab-04_10_10.png)

-From the error above create a network SG and then an inbound security rules to allow RDP

![](Image/a-6urelab-04_10_14.png)

![](Image/a-6urelab-04_10_15.png)

![](Image/a-6urelab-04_10_20.png)

![](Image/a-6urelab-04_10_22.png)


-Associate the NGS to the nics

![](Image/a-6urelab-04_10_23.png)

![](Image/a-6urelab-04_10_24.png)

![](Image/a-6urelab-04_10_26.png)


Start both VMs
download the RDP

VM0

![](Image/a-6urelab-04-06_12_35.png)

![](Image/a-6urelab-04-06_12_37.png)


VM1

![](Image/a-6urelab-04-06_12_33.png)

![](Image/a-6urelab-04-06_12_34.png)


# TASK 5: Configure Azure DNS for internal name resolution

In this task, you will configure DNS name resolution within a virtual network by using Azure private DNS zones.

-Create Private DNS zones for internal name resolution

![](Image/a-6urelab-04-06_01_00_14.png)

![](Image/a-6urelab-04-06_01_02_44.png)

![](Image/a-6urelab-04-06_01_03_45.png)

Link

![](Image/a-6urelab-04-06_01_06_15.png)

![](Image/a-6urelab-04-06_01_07_44.png)

![](Image/a-6urelab-04-06_01_08_26.png)

![](Image/a-6urelab-04-06_01_09_50.png)

![](Image/a-6urelab-04-06_01_10_02.png)

Connect to the RDP session

Note: I found the pasword within the ARM template

    Student
    Pa55w.rd1234

Verify DNS resolution is woking

![](Image/a-6urelab-04-06_01_22_02.png)


# Task 6: configure Azure DNS for external name resolution

VM public iP

    az104-04-vm0 20.172.148.64
    az104-04-vm1 20.51.160.144

![](Image/a-6urelab-04-06_01_28_17.png)

![](Image/a-6urelab-04-06_01_29_14.png)

![](Image/a-6urelab-04-06_01_30_05.png)

![](Image/a-6urelab-04-06_01_30_29.png)

![](Image/a-6urelab-04-06_01_46_21.png)

![](Image/a-6urelab-04-06_01_37_28.png)

![](Image/a-6urelab-04-06_01_47_42.png)

![](Image/a-6urelab-04-06_01_47_58.png)


Verify that the output of the command includes the public IP address of az104-04-vm1.

![](Image/a-6urelab-04-06_01_55_27.png)


Completion map

![](Image/a-6urelab-04-06_02_17_57.png)

![](Image/a-6urelab-04-06_02_19_05.png)



# Clean up

-List all resource groups created

    Get-AzResourceGroup -Name 'az104-04*'

![](Image/a-6urelab-04-06_02_39_59.png)

-Delete all resource groups created by this lab

    Get-AzResourceGroup -Name 'az104-04*' | Remove-AzResourceGroup -Force -AsJob

![](Image/a-6urelab-04-06_02_41_06.png)


resource before deletion

![](Image/a-6urelab-04-06_02_43_58.png)


![](Image/a-6urelab-04-06_02_48_46.png)

![](Image/a-6urelab-04-06_02_49_28.png)

<img src="Image/a-6urelab-04-06_02_49_28.png" width="1000" >

