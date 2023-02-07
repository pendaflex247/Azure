
# Objectives
In this lab, you will:

    Task 1: Create and configure a virtual network
    Task 2: Deploy virtual machines into the virtual network
    Task 3: Configure private and public IP addresses of Azure VMs
    Task 4: Configure network security groups
    Task 5: Configure Azure DNS for internal name resolution
    Task 6: Configure Azure DNS for external name resolution

# Network Map

<img src="Image/az104lab04.png" width="780" >

# Task 1: Create and configure a virtual network with two subnets

Create a resource group
-

<img src="Image/a-6104lab04_11_55.png" width="780" >

<img src="Image/a-6104lab04_11_56.png" width="780" >

<img src="Image/a-6104lab04_12_03.png" width="780" >


Create a virtual network
-

<img src="Image/a-6urelab-04_12_06.png" width="780" >

<img src="Image/a-6urelab-04_12_14.png" width="780" >

<img src="Image/a-6urelab-04_12_22.png" width="780" >


Create two subnets
-

    -ipadd space 10.40.0.0/20
    -subnet0 10.40.0.0/24
    -subnet1 10.40.1.0/24


<img src="Image/a-6urelab-04_12_37.png" width="780" >

<img src="Image/a-6urelab-04_12_38.png" width="780" >

<img src="Image/a-6urelab-04_12_39.png" width="780" >


Create Virtual machine in both subnets using ARM
-

<img src="Image/a-6urelab-04_02_18.png" width="780" >

<img src="Image/a-6urelab-04_02_20.png" width="780" >


-Upload the templates

<img src="Image/a-6urelab-04_02_45.png" width="780" >


# TASK 2: Deploy two virtual machines using the template and paramenter files on powershell

    $rgName = 'az104-04-rg1'

    New-AzResourceGroupDeployment `
        -ResourceGroupName $rgName `
        -TemplateFile $HOME/az104-04-vms-loop-template.json `
        -TemplateParameterFile $HOME/az104-04-vms-loop-parameters.json


<img src="Image/a-6urelab-04_02_48.png" width="780" >

<img src="Image/a-6urelab-04_02_50.png" width="780" >

<img src="Image/a-6urelab-04_02_52.png" width="780" >

-Verify the vm were created

<img src="Image/a-6urelab-04_02_56.png" width="780" >

# TASK 3: Configure private and public IP addresses of Azure VMs

<img src="Image/a-6urelab-04_06_00.png" width="780" >

<img src="Image/a-6urelab-04_06_01.png" width="780" >

<img src="Image/a-6urelab-04_06_06.png" width="780" >

<img src="Image/a-6urelab-04_06_07.png" width="780" >

<img src="Image/a-6urelab-04_06_01.png" width="780" >

<img src="Image/a-6urelab-04_06_17.png" width="780" >

<img src="Image/a-6urelab-04_06_18.png" width="780" >

<img src="Image/a-6urelab-04_09_58.png" width="780" >

<img src="Image/a-6urelab-04_09_59.png" width="780" >


# TASK 4: Configure network security groups  
-In order to allow for restricted connectivity to Azure virtual machines.

<img src="Image/a-6urelab-04_10_09.png" width="780" >

<img src="Image/a-6urelab-04_10_10.png" width="780" >

-From the error above create a network SG and then an inbound security rules to allow RDP


<img src="Image/a-6urelab-04_10_14.png" width="780" >

<img src="Image/a-6urelab-04_10_15.png" width="780" >

<img src="Image/a-6urelab-04_10_20.png" width="780" >

<img src="Image/a-6urelab-04_10_22.png" width="780" >


-Associate the NGS to the nics

<img src="Image/a-6urelab-04_10_23.png" width="780" >

<img src="Image/a-6urelab-04_10_24.png" width="780" >

<img src="Image/a-6urelab-04_10_26.png" width="780" >


Start both VMs
download the RDP

VM0

<img src="Image/a-6urelab-04-06_12_35.png" width="780" >

<img src="Image/a-6urelab-04-06_12_37.png" width="780" >


VM1

<img src="Image/a-6urelab-04-06_12_33.png" width="780" >

<img src="Image/a-6urelab-04-06_12_34.png" width="780" >


# TASK 5: Configure Azure DNS for internal name resolution

In this task, you will configure DNS name resolution within a virtual network by using Azure private DNS zones.

-Create Private DNS zones for internal name resolution

<img src="Image/a-6urelab-04-06_01_00_14.png" width="780" >

<img src="Image/a-6urelab-04-06_01_02_44.png" width="780" >

<img src="Image/a-6urelab-04-06_01_03_45.png" width="780" >


Link


<img src="Image/a-6urelab-04-06_01_06_15.png" width="780" >

<img src="Image/a-6urelab-04-06_01_07_44.png" width="780" >

<img src="Image/a-6urelab-04-06_01_08_26.png" width="780" >

<img src="Image/a-6urelab-04-06_01_09_50.png" width="780" >

<img src="Image/a-6urelab-04-06_01_10_02.png" width="780" >



Connect to the RDP session

Note: I found the pasword within the ARM template

    Student
    Pa55w.rd1234

Verify DNS resolution is woking


<img src="Image/a-6urelab-04-06_01_22_02.png" width="780" >


# Task 6: configure Azure DNS for external name resolution

VM public iP

    az104-04-vm0 20.172.148.64
    az104-04-vm1 20.51.160.144


<img src="Image/a-6urelab-04-06_01_28_17.png" width="780" >

<img src="Image/a-6urelab-04-06_01_29_14.png" width="780" >

<img src="Image/a-6urelab-04-06_01_30_05.png" width="780" >

<img src="Image/a-6urelab-04-06_01_30_29.png" width="780" >

<img src="Image/a-6urelab-04-06_01_46_21.png" width="780" >

<img src="Image/a-6urelab-04-06_01_37_28.png" width="780" >

<img src="Image/a-6urelab-04-06_01_47_42.png" width="780" >

<img src="Image/a-6urelab-04-06_01_47_58.png" width="780" >


Verify that the output of the command includes the public IP address of az104-04-vm1.

<img src="Image/a-6urelab-04-06_01_55_27.png" width="780" >

# Completion map

<img src="Image/a-6urelab-04-06_02_17_57.png" width="780" >


# Clean up

-List all resource groups created

    Get-AzResourceGroup -Name 'az104-04*'

<img src="Image/a-6urelab-04-06_02_39_59.png" width="780" >

-Delete all resource groups created by this lab

    Get-AzResourceGroup -Name 'az104-04*' | Remove-AzResourceGroup -Force -AsJob

<img src="Image/a-6urelab-04-06_02_41_06.png" width="780" >

-resource before clean up

<img src="Image/a-6urelab-04-06_02_43_58.png" width="780" >

-After Clean up

<img src="Image/a-6urelab-04-06_02_49_28.png" width="780" >

