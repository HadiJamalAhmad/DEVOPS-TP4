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
data.azurerm_resource_group.tp4: Reading...
azurerm_public_ip.myterraformpublicip: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/publicIPAddresses/myPublicIP_]
data.azurerm_virtual_network.tp4: Reading...
azurerm_network_security_group.myterraformnsg: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkSecurityGroups/myNetworkSecurityGroup_Hadi]
data.azurerm_resource_group.tp4: Read complete after 0s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2]
random_id.randomId: Refreshing state... [id=eQgJE6ACAFU]
data.azurerm_virtual_network.tp4: Read complete after 0s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network]
data.azurerm_subnet.tp4: Read complete after 1s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network/subnets/internal]
azurerm_network_interface.myterraformnic: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkInterfaces/myNIC]
azurerm_network_interface_security_group_association.example: Refreshing state... [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkInterfaces/myNIC|/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkSecurityGroups/myNetworkSecurityGroup_Hadi]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following        
symbols:
  + create

Terraform will perform the following actions:

  # azurerm_linux_virtual_machine.devops-20211136 will be created
  + resource "azurerm_linux_virtual_machine" "devops-20211136" {
      + admin_username                  = "devops"
      + allow_extension_operations      = true
      + computer_name                   = "myvm"
      + disable_password_authentication = true
      + extensions_time_budget          = "PT1H30M"
      + id                              = (known after apply)
      + location                        = "francecentral"
      + max_bid_price                   = -1
      + name                            = "myVM"
      + network_interface_ids           = [
          + "/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/networkInterfaces/myNIC",
        ]
      + patch_mode                      = "ImageDefault"
      + platform_fault_domain           = -1
      + priority                        = "Regular"
      + private_ip_address              = (known after apply)
      + private_ip_addresses            = (known after apply)
      + provision_vm_agent              = true
      + public_ip_address               = (known after apply)
      + public_ip_addresses             = (known after apply)
      + resource_group_name             = "devops-TP2"
      + size                            = "Standard_D2s_v3"
      + virtual_machine_id              = (known after apply)

      + admin_ssh_key {
          + public_key = <<-EOT
                ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCkgqV92+TB0pW6oVL8Gx8fm1C0JmJBfrfgekswIgSWJD2iAACzt/R1uYXvWzk5sIa/i+t56/qCDF8yzI08+LJCrfrvijNxEP2grg/+KFJTTDMPX5DiPahwuWN0yxPP3skiUHpCZ2829mNWoYHIAF3AtyK4FCWXeB9IFumMPW9jxzzzHEkPWErLxPdpWJ4m/UsXBN5Nnrvz+4oiZtGsctsex9KrZE9SsxtupVj6fQIOi2E9yfTcsF+t8KPEY6ooL6MD6vZYGvtnLH9uH4F/NSK3H7hlraXyxF5iYyzalfXCmUZVKZdH15Wl2rvCkWkrAeWSvbUIE6D+zpvbX1cQriUPhzPEv4i1N4yUMi3NiE7YU/fAhT1zRGncNfYywZ9MM/hL2orpkVlNnpNLenZ77NkWntDYOeb0FeqcqT35msAicERlyszeZiC5auVIZLEYk1tqKbGFjT/+ByMl0UnhTTdbpCgUu4DqyPp41KWXqbAbfjlPeKG2aDVrIRkFChibw64CZfrewngMMUkoXwASn3kkJiNFyfPhChcY/nwHhzWgZJOeZQr7DY66SMBnmZm/TAb8RaQCeeDsDF1dpA53bjyG/6JwyPVnyTY/8jrklb2kxHftkSLjytJR1ibNewBYQbOycXNRGHvlwpLl52W5xNWxAhtv5ldW6UCom/Wyr8BKXQ==
            EOT
          + username   = "devops"
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
          + sku       = "16.04-LTS"
          + version   = "latest"
        }

      + termination_notification {
          + enabled = (known after apply)
          + timeout = (known after apply)
        }
    }

Plan: 1 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

azurerm_linux_virtual_machine.devops-20211136: Creating...
azurerm_linux_virtual_machine.devops-20211136: Still creating... [10s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still creating... [20s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still creating... [30s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Still creating... [40s elapsed]
azurerm_linux_virtual_machine.devops-20211136: Creation complete after 49s [id=/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Compute/virtualMachines/myVM]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

Outputs:

virtual_network_id = "/subscriptions/765266c6-9a23-4638-af32-dd1e32613047/resourceGroups/devops-TP2/providers/Microsoft.Network/virtualNetworks/example-network"
hadi@LAPTOP-ADEE62RQ:/mnt/c/Users/hadij/Downloads/Devops/TP4$
