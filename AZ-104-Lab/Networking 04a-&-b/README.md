
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

# Task 1: Create and configure a virtual network with two subnets

Create a resource group
-

![](Image/a-6104lab04_11_55.png)

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




