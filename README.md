# microcks-azure

Templates and scripts for easy setup on Azure.

## Microcks Azure demo

Simplistic template for creating an all-in-one VM on Azure. All the pre-requisites are installed and set up on a Standard B2s + Ubuntu 18.04 LTS which is very cheap.

**Note:** This is a demonstration purpose configuration that - obviously - is not highly available and will not scale to hundreds of mocks and invocations. However, it will allow you to evaluate Microcks.

Simply click on `Deploy to Azure` then you will be redirected to your Azure account:

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrocks%2Fmicrocks-azure%2Fmaster%2Fazure-demo-template.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fmicrocks%2Fmicrocks-azure%2Fmaster%2Fazure-demo-template.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

### Template Parameters

This template is just using 4 parameters:
* `adminUsername` will be the username for SSH login to the created VM,
* `sshKeyData` will be the corresponding Public SSH key for administrator access to VM,
* `vmName` should be the globally unique name for this VM. It will be used for complete FQDN name creation,
* `microcksVersion` is the tagged version of Microcks you want to install. Default is `latest` which ... is the latest!

### Start microcks

Once VM is created on Azure, just connect to it and start Microcks using these commands:

```
$ ssh -A <adminUsername>@<VM Public IP>
$ cd /opt/microcks/install/docker-compose
$ sudo docker-compose -f microcks.yml up -d
```

Wait for a few seconds everything has started and then test Microcks!
