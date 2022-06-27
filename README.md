# DEVOPS-TP4


# terraform init

hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$ terraform init

Initializing the backend...

Initializing provider plugins...
- Finding latest version of hashicorp/random...
- Finding latest version of hashicorp/tls...
- Finding hashicorp/azurerm versions matching "3.0.0"...
- Installing hashicorp/tls v3.4.0...
- Installed hashicorp/tls v3.4.0 (signed by HashiCorp)
- Installing hashicorp/azurerm v3.0.0...
- Installed hashicorp/azurerm v3.0.0 (signed by HashiCorp)
- Installing hashicorp/random v3.3.2...
- Installed hashicorp/random v3.3.2 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$



# terraform plan


hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$ terraform plan
data.azurerm_virtual_network.tp4: Reading...
data.azurerm_subnet.tp4: Reading...
data.azurerm_resource_group.tp4: Reading...
data.azurerm_virtual_network.tp4: Read complete after 0s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network]
data.azurerm_subnet.tp4: Read complete after 0s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network/subnets/internal]
data.azurerm_resource_group.tp4: Read complete after 1s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following        
symbols:
  + create

Terraform will perform the following actions:

  # azurerm_linux_virtual_machine.myterraformvm will be created
  + resource "azurerm_linux_virtual_machine" "myterraformvm" {
      + admin_username                  = "azureuser"
      + allow_extension_operations      = true
      + computer_name                   = "myvm"
      + disable_password_authentication = true
      + extensions_time_budget          = "PT1H30M"
      + id                              = (known after apply)
      + location                        = "francecentral"
      + max_bid_price                   = -1
      + name                            = "myVM"
      + network_interface_ids           = (known after apply)
      + patch_mode                      = "ImageDefault"
      + platform_fault_domain           = -1
      + priority                        = "Regular"
      + private_ip_address              = (known after apply)
      + private_ip_addresses            = (known after apply)
      + provision_vm_agent              = true
      + public_ip_address               = (known after apply)
      + public_ip_addresses             = (known after apply)
      + resource_group_name             = "devops-TP2"
      + size                            = "Standard_DS1_v2"
      + virtual_machine_id              = (known after apply)

      + admin_ssh_key {
          + public_key = (known after apply)
          + username   = "azureuser"
        }

      + os_disk {
          + caching                   = "ReadWrite"
          + disk_size_gb              = (known after apply)
          + name                      = "myOsDisk"
          + storage_account_type      = "Premium_LRS"
          + write_accelerator_enabled = false
        }

      + source_image_reference {
          + offer     = "UbuntuServer"
          + publisher = "Canonical"
          + sku       = "18.04-LTS"
          + version   = "latest"
        }

      + termination_notification {
          + enabled = (known after apply)
          + timeout = (known after apply)
        }
    }

  # azurerm_network_interface.myterraformnic will be created
  + resource "azurerm_network_interface" "myterraformnic" {
      + applied_dns_servers           = (known after apply)
      + dns_servers                   = (known after apply)
      + enable_accelerated_networking = false
      + enable_ip_forwarding          = false
      + id                            = (known after apply)
      + internal_dns_name_label       = (known after apply)
      + internal_domain_name_suffix   = (known after apply)
      + location                      = "francecentral"
      + mac_address                   = (known after apply)
      + name                          = "myNIC"
      + private_ip_address            = (known after apply)
      + private_ip_addresses          = (known after apply)
      + resource_group_name           = "devops-TP2"
      + virtual_machine_id            = (known after apply)

      + ip_configuration {
          + gateway_load_balancer_frontend_ip_configuration_id = (known after apply)
          + name                                               = "myNicConfiguration"
          + primary                                            = (known after apply)
          + private_ip_address                                 = (known after apply)
          + private_ip_address_allocation                      = "Dynamic"
          + private_ip_address_version                         = "IPv4"
          + public_ip_address_id                               = (known after apply)
          + subnet_id                                          = "/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network/subnets/internal"
        }
    }

  # azurerm_network_interface_security_group_association.example will be created
  + resource "azurerm_network_interface_security_group_association" "example" {
      + id                        = (known after apply)
      + network_interface_id      = (known after apply)
      + network_security_group_id = (known after apply)
    }

  # azurerm_network_security_group.myterraformnsg will be created
  + resource "azurerm_network_security_group" "myterraformnsg" {
      + id                  = (known after apply)
      + location            = "francecentral"
      + name                = "myNetworkSecurityGroup"
      + resource_group_name = "devops-TP2"
      + security_rule       = [
          + {
              + access                                     = "Allow"
              + description                                = ""
              + destination_address_prefix                 = "*"
              + destination_address_prefixes               = []
              + destination_application_security_group_ids = []
              + destination_port_range                     = "22"
              + destination_port_ranges                    = []
              + direction                                  = "Inbound"
              + name                                       = "SSH"
              + priority                                   = 1001
              + protocol                                   = "Tcp"
              + source_address_prefix                      = "*"
              + source_address_prefixes                    = []
              + source_application_security_group_ids      = []
              + source_port_range                          = "*"
              + source_port_ranges                         = []
            },
        ]
    }

  # azurerm_public_ip.myterraformpublicip will be created
  + resource "azurerm_public_ip" "myterraformpublicip" {
      + allocation_method       = "Dynamic"
      + fqdn                    = (known after apply)
      + id                      = (known after apply)
      + idle_timeout_in_minutes = 4
      + ip_address              = (known after apply)
      + ip_version              = "IPv4"
      + location                = "francecentral"
      + name                    = "myPublicIP_"
      + resource_group_name     = "devops-TP2"
      + sku                     = "Basic"
      + sku_tier                = "Regional"
    }

  # random_id.randomId will be created
  + resource "random_id" "randomId" {
      + b64_std     = (known after apply)
      + b64_url     = (known after apply)
      + byte_length = 8
      + dec         = (known after apply)
      + hex         = (known after apply)
      + id          = (known after apply)
      + keepers     = {
          + "resource_group" = "devops-TP2"
        }
    }

  # tls_private_key.example_ssh will be created
  + resource "tls_private_key" "example_ssh" {
      + algorithm                     = "RSA"
      + ecdsa_curve                   = "P224"
      + id                            = (known after apply)
      + private_key_openssh           = (sensitive value)
      + private_key_pem               = (sensitive value)
      + public_key_fingerprint_md5    = (known after apply)
      + public_key_fingerprint_sha256 = (known after apply)
      + public_key_openssh            = (known after apply)
      + public_key_pem                = (known after apply)
      + rsa_bits                      = 4096
    }

Plan: 7 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + virtual_network_id = "/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network"

──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── 

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run "terraform 
apply" now.
hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$





# terraform apply


hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$ terraform apply
tls_private_key.example_ssh: Refreshing state... [id=bc1753b7d31efc59ceb094e1f9738bae5259836e]
data.azurerm_subnet.tp4: Reading...
data.azurerm_virtual_network.tp4: Reading...
data.azurerm_resource_group.tp4: Reading...
azurerm_public_ip.myterraformpublicip: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/publicIPAddresses/myPublicIP_]
azurerm_network_security_group.myterraformnsg: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkSecurityGroups/myNetworkSecurityGroup_Hadi]
data.azurerm_resource_group.tp4: Read complete after 1s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2]
random_id.randomId: Refreshing state... [id=eQgJE6ACAFU]
data.azurerm_subnet.tp4: Read complete after 1s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network/subnets/internal]
azurerm_network_interface.myterraformnic: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkInterfaces/myNIC]
data.azurerm_virtual_network.tp4: Read complete after 1s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network]
azurerm_network_interface_security_group_association.example: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkInterfaces/myNIC|/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkSecurityGroups/myNetworkSecurityGroup_Hadi]
azurerm_linux_virtual_machine.devops-20211136: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Compute/virtualMachines/myVM]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following        
symbols:
-/+ destroy and then create replacement

Terraform will perform the following actions:

  # azurerm_linux_virtual_machine.devops-20211136 must be replaced
-/+ resource "azurerm_linux_virtual_machine" "devops-20211136" {
      - encryption_at_host_enabled      = false -> null
      ~ id                              = "/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Compute/virtualMachines/myVM" -> (known after apply)
      ~ name                            = "myVM" -> "devops-20211136" # forces replacement
      ~ private_ip_address              = "10.3.1.7" -> (known after apply)
      ~ private_ip_addresses            = [
          - "10.3.1.7",
        ] -> (known after apply)
      ~ public_ip_address               = "20.111.29.11" -> (known after apply)
      ~ public_ip_addresses             = [
          - "20.111.29.11",
        ] -> (known after apply)
      - secure_boot_enabled             = false -> null
      - tags                            = {} -> null
      ~ virtual_machine_id              = "7ccee57e-ccb8-4f00-8917-f1aa54fccad5" -> (known after apply)
      - vtpm_enabled                    = false -> null
        # (14 unchanged attributes hidden)


      ~ os_disk {
          ~ disk_size_gb              = 30 -> (known after apply)
            name                      = "myOsDisk"
            # (3 unchanged attributes hidden)
        }


      + termination_notification {
          + enabled = (known after apply)
          + timeout = (known after apply)
        }
        # (2 unchanged blocks hidden)
    }

Plan: 1 to add, 0 to change, 1 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

azurerm_linux_virtual_machine.devops-20211136: Destroying... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Compute/virtualMachines/myVM]
azurerm_linux_virtual_machine.devops-20211136: Still destroying... [id=/subscriptions/765266c6-9a23-4638-af32-...Microsoft.Compute/virtualMachines/myVM, 10s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still destroying... [id=/subscriptions/765266c6-9a23-4638-af32-...Microsoft.Compute/virtualMachines/myVM, 20s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still destroying... [id=/subscriptions/765266c6-9a23-4638-af32-...Microsoft.Compute/virtualMachines/myVM, 30s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still destroying... [id=/subscriptions/765266c6-9a23-4638-af32-...Microsoft.Compute/virtualMachines/myVM, 40s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still destroying... [id=/subscriptions/765266c6-9a23-4638-af32-...Microsoft.Compute/virtualMachines/myVM, 50s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still destroying... [id=/subscriptions/765266c6-9a23-4638-af32-...Microsoft.Compute/virtualMachines/myVM, 1m0s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still destroying... [id=/subscriptions/765266c6-9a23-4638-af32-...Microsoft.Compute/virtualMachines/myVM, 1m10s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Destruction complete after 1m16s
azurerm_linux_virtual_machine.devops-20211136: Creating...
azurerm_linux_virtual_machine.devops-20211136: Still creating... [10s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still creating... [20s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still creating... [30s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still creating... [40s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Creation complete after 46s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Compute/virtualMachines/devops-20211136]

Apply complete! Resources: 1 added, 0 changed, 1 destroyed.

Outputs:

virtual_network_id = "/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network"
hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$



# terraform output

hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$ terraform output
virtual_network_id = "/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network"



# Se connecter à la VM avec SSH

hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$ terraform init

Initializing the backend...

Initializing provider plugins...
- Reusing previous version of hashicorp/azurerm from the dependency lock file
- Reusing previous version of hashicorp/random from the dependency lock file
- Reusing previous version of hashicorp/tls from the dependency lock file
- Using previously-installed hashicorp/tls v3.4.0
- Using previously-installed hashicorp/azurerm v3.0.0
- Using previously-installed hashicorp/random v3.3.2

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$ terraform plan -out main.tfplan
tls_private_key.example_ssh: Refreshing state... [id=bc1753b7d31efc59ceb094e1f9738bae5259836e]
data.azurerm_subnet.tp4: Reading...
data.azurerm_virtual_network.tp4: Reading...
data.azurerm_resource_group.tp4: Reading...
azurerm_public_ip.myterraformpublicip: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/publicIPAddresses/myPublicIP_]
azurerm_network_security_group.myterraformnsg: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkSecurityGroups/myNetworkSecurityGroup_Hadi]
data.azurerm_resource_group.tp4: Read complete after 0s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2]
random_id.randomId: Refreshing state... [id=eQgJE6ACAFU]
data.azurerm_subnet.tp4: Read complete after 0s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network/subnets/internal]
azurerm_network_interface.myterraformnic: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkInterfaces/myNIC]
data.azurerm_virtual_network.tp4: Read complete after 0s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network]
azurerm_network_interface_security_group_association.example: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkInterfaces/myNIC|/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkSecurityGroups/myNetworkSecurityGroup_Hadi]
azurerm_linux_virtual_machine.devops-20211136: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Compute/virtualMachines/devops-20211136]

Changes to Outputs:
  + public_ip_address   = "20.216.169.42"
  + resource_group_name = "devops-TP2"
  + tls_private_key     = (sensitive value)

You can apply this plan to save these new output values to the Terraform state, without changing any real infrastructure.

──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── 

Saved the plan to: main.tfplan

To perform exactly these actions, run the following command to apply:
    terraform apply "main.tfplan"
hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$

