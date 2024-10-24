1. create a resource group
2. create a vm
   * 2.1 Azure cli user data
  
 '''
#!/bin/bash
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release -y
sudo mkdir -p /etc/apt/keyrings
curl -sLS https://packages.microsoft.com/keys/microsoft.asc |
  gpg --dearmor | sudo tee /etc/apt/keyrings/microsoft.gpg > /dev/null
sudo chmod go+r /etc/apt/keyrings/microsoft.gpg
AZ_DIST=$(lsb_release -cs)
echo "Types: deb
URIs: https://packages.microsoft.com/repos/azure-cli/
Suites: ${AZ_DIST}
Components: main
Architectures: $(dpkg --print-architecture)
Signed-by: /etc/apt/keyrings/microsoft.gpg" | sudo tee /etc/apt/sources.list.d/azure-cli.sources
sudo apt-get update
sudo apt-get install azure-cli -y
 '''

3. create a azure cli

4. Commands to create AKS cluster from bash (linux/mac)
  '''
   # variables 
export MY_RESOURCE_GROUP_NAME="myAKSResourceGroup"
export REGION="eastus"
export MY_AKS_CLUSTER_NAME="myAKSCluster"
export MY_DNS_LABEL="mydnslabel"
  '''

  '''
  # Create a resource group
az group create --name $MY_RESOURCE_GROUP_NAME --location $REGION
az aks create --resource-group $MY_RESOURCE_GROUP_NAME --name $MY_AKS_CLUSTER_NAME --node-count 1 --node-vm-size "Standard_B2ms" --generate-ssh-keys
# install kubectl
az aks install-cli 
# get kube config
az aks get-credentials --resource-group $MY_RESOURCE_GROUP_NAME --name $MY_AKS_CLUSTER_NAME
  '''



