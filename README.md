# azurelandingzone


- CentOS VM
신규 CentOS 7.5 VM 설치
https://github.com/bedro96/tf-centos
 
- CentOS VM에 Docker 설치하기
$ sudo yum install -y yum-utils

$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
$ sudo yum install docker-ce docker-ce-cli containerd.io
$ sudo systemctl start docker
$ sudo usermod -aG docker $USER

logoff and login again.
    
- rover 
https://hub.docker.com/r/aztfmod/rover/tags
```
docker pull docker pull aztfmod/rover:2005.1510
```

- landing zone
git clone https://github.com/Azure/caf-terraform-landingzones.git

- docker image run with volume mount
```
docker run -v /home/centadmin/caf-terraform-landingzones/landingzones:/tf/caf/landingzones -it --name rover aztfmod/rover:2005.1510
```

-- run this command
login with rover
```
rover login microsoft.com 05be085b-86ea-4336-addc-38fd56051a9e
```
- run lauchpad
```
launchpad /tf/launchpads/launchpad_opensource_light apply -var location=koreacentral        
```
The Result 
```
Apply complete! Resources: 35 added, 0 changed, 0 destroyed.

The state of your infrastructure has been saved to the path
below. This state is required to modify and destroy your
infrastructure, so keep it safe. To inspect the complete state
use the `terraform show` command.

State path: terraform.tfstate

Outputs:

container = level0
devops_client_secret = <sensitive>
diagnostics = <sensitive>
keyvault_id = /subscriptions/05be085b-86ea-4336-addc-38fd56051a9e/resourceGroups/zlia-rg-terraform-state-rmkEGsvdXPSFd8Xku0zFkUkpfl5UEyzTdtoEsO0uHGqMSqvcmGHW12Je/providers/Microsoft.KeyVault/vaults/gzlia-kv-level0-upkqjafa
launchpad_application_id = <sensitive>
log_analytics = <sensitive>
prefix = zlia
resource_group = zlia-rg-terraform-state-rmkEGsvdXPSFd8Xku0zFkUkpfl5UEyzTdtoEsO0uHGqMSqvcmGHW12Je
storage_account_name = zliastlevel0fshfbqlcpmvj
tfstate-blob-name = launchpad_opensource_light.tfstate
tfstate_map = {
  "container" = "level0"
  "prefix" = "zlia"
  "resource_group" = "zlia-rg-terraform-state-rmkEGsvdXPSFd8Xku0zFkUkpfl5UEyzTdtoEsO0uHGqMSqvcmGHW12Je"
  "storage_account_name" = "zliastlevel0fshfbqlcpmvj"
}
Terraform apply return code: 0
@calling workspace_create
 Calling workspace_create function
 Create sandpit workspace

{
  "created": true
}

@calling workspace_create
 Calling workspace_create function
 Create level0 workspace

{
  "created": false
}

@calling upload_tfstate
Moving launchpad to the cloud
 - storage_account_name: zliastlevel0fshfbqlcpmvj
 - resource_group: zlia-rg-terraform-state-rmkEGsvdXPSFd8Xku0zFkUkpfl5UEyzTdtoEsO0uHGqMSqvcmGHW12Je
 - storage_key: retrieved
{
  "etag": "\"0x8D815F669DDEBAF\"",
  "lastModified": "2020-06-21T15:18:55+00:00"
}

You can deploy a landingzone with the rover by running:
  rover [landingzone_folder_name] [plan|apply|destroy]

List of the landingzones loaded in the rover:
/tf/caf/landingzones/landingzone_caf_foundations
/tf/caf/landingzones/landingzone_hub_spoke
/tf/caf/landingzones/landingzone_secure_vnet_dmz
/tf/caf/landingzones/landingzone_starter
/tf/caf/landingzones/landingzone_vdc_demo

@calling clean_up_variables
cleanup variables
```
- Installing the first CAF foundation 
```
rover /tf/caf/landingzones/landingzone_caf_foundations apply
```
