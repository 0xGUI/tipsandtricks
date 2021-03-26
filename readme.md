
---

# terraform
## Use Infrastructure as Code to provision and manage any cloud, infrastructure, or service
## links:
https://www.terraform.io/downloads.html  
https://releases.hashicorp.com/terraform/  
	
## instructions:
```
version="0.12.18"  
app="terraform"  
wget "https://releases.hashicorp.com/${app}/${version}/${app}_${version}_linux_amd64.zip" -O ${app}_${version}.zip  
unzip ${app}_${version}.zip  
sudo mkdir -p /tools/${app}  
sudo cp ${app} /tools/${app}/${app}_${version}  
sudo ln -sfn /tools/${app}/${app}_${version} /usr/local/bin/${app}  
```
### Test:  
`terraform version`  

---

# vault
## Manage Secrets and Protect Sensitive Data
## links:   
https://www.vaultproject.io/downloads/  
https://releases.hashicorp.com/vault/  
https://releases.hashicorp.com/vault/1.3.1/vault_1.3.1_linux_amd64.zip  
  
## instructions:  
```
version="1.3.1"  
app="vault"  
wget "https://releases.hashicorp.com/vault/${version}/${app}_${version}_linux_amd64.zip" -O ${app}_${version}.zip  
unzip ${app}_${version}.zip  
sudo mkdir -p /tools/${app}  
sudo cp ${app} /tools/${app}/${app}_${version}  
sudo ln -sfn /tools/${app}/${app}_${version} /usr/local/bin/${app}  
```  
### test:
`vault version`  

------------------------------------------------------------------------------------------
	
# helm
## Helm is a tool for managing Charts. Charts are packages of pre-configured Kubernetes resources.
## links:   
https://github.com/helm/helm/releases  
https://github.com/helm/helm/releases/latest  
https://hub.helm.sh/  

	
## instructions:
```
version="3.2.1"
app="helm"
wget "https://get.helm.sh/${app}-v${version}-linux-amd64.tar.gz" -O ${app}_${version}.tar.gz
tar -zxvf ${app}_${version}.tar.gz
sudo mkdir -p /tools/${app}
sudo cp linux-amd64/${app} /tools/${app}/${app}_${version}
sudo ln -sfn /tools/${app}/${app}_${version} /usr/local/bin/${app}
``` 
### test:
`helm version`  

------------------------
## helm diff: 

### Install:
`helm plugin install https://github.com/databus23/helm-diff --version master`

### Usage:
`helm diff upgrade --allow-unreleased nginx-ingress stable/nginx-ingress -f values.yaml`

#### link: https://github.com/databus23/helm-diff
------------------------------------------------------------------------------------------

# golang-go
## Go is an open source programming language that makes it easy to build simple, reliable, and efficient software.
## link: 
https://golang.org/dl/
## instructions:
apt-get: `sudo apt-get install golang-go`

or manual:
```
version="1.13.6"
app="go"
wget "https://dl.google.com/${app}/${app}${version}.linux-amd64.tar.gz" -O ${app}_${version}.tar.gz
sudo mkdir -p /tools/${app}_${version}/
sudo tar -C /tools/${app}_${version}/ -zxf ${app}_${version}.tar.gz
sudo ln -sfn /tools/${app}_${version}/ /tools/${app}/
sudo ln -sfn /tools/${app}/bin/${app} /usr/local/bin/${app}
```

## test: 
`go version`

------------------------------------------------------------------------------------------

# Google tools: gcloud, kubectl, gsutil
## Gcloud command-line tool
## links:
https://cloud.google.com/sdk/docs/downloads-apt-get  
## instructions:
```
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
sudo apt-get install apt-transport-https ca-certificates gnupg
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
sudo apt-get update && sudo apt-get install google-cloud-sdk kubectl -y
```

## test:
`gcloud version`  

------------------------------------------------------------------------------------------

# zsh
## Alternative shell
`apt-get install zsh`  

### test:
`zsh --version`  
  

## add-ons:
### ohmyzsh - Oh My Zsh will not make you a 10x developer...but you may feel like one.
links: https://ohmyz.sh  
instructions:  
`sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`


### powerlevel10k - A fast reimplementation of Powerlevel9k ZSH theme 
## links:
https://github.com/romkatv/powerlevel10k

## instructions:
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
Set ZSH_THEME=powerlevel10k/powerlevel10k in your ~/.zshrc.
ohmyzsh
powerlevel10k
```  

### Zsh auto-suggestions
https://github.com/zsh-users/zsh-autosuggestions


## fzf - A command-line fuzzy finder 

## links:
https://github.com/junegunn/fzf

## instructions:
```
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

### test:
`fzf --version`

------------------------------------------------------------------------------------------

# kubectx/kubens
## Faster way to switch between clusters and namespaces in kubectl 
## links:
https://github.com/ahmetb/kubectx  

## test:
```
kubectx -h  
kubens -h  
```

-----------------------------------------

# kubectl-aliases
## This repository contains a script to generate hundreds of convenient shell aliases for kubectl, so you no longer need to spell out every single command and --flag over and over again.
## link: 
https://github.com/ahmetb/kubectl-aliases

## instructions:
```
git clone https://github.com/ahmetb/kubectl-aliases.git
cp kubectl-aliases/.kubectl_aliases ~

cat << FOE >> ~/.zshrc

#kubectl_aliases function to print command
function kubectl() { echo "+ kubectl $@">&2; command kubectl $@; }

#kubectl_aliases
[ -f ~/.kubectl_aliases ] && source ~/.kubectl_aliases
FOE

cat << FOE >> ~/.bashrc

#kubectl_aliases function to print command
function kubectl() { echo "+ kubectl $@">&2; command kubectl $@; }

#kubectl_aliases
[ -f ~/.kubectl_aliases ] && source ~/.kubectl_aliases
FOE
```

## test: 
`k version`

------------------------------------------------------------------------------------------

# stern

## Stern allows you to tail multiple pods on Kubernetes and multiple containers within the pod
## link: 
https://github.com/wercker/stern  

## instructions:
```
version="1.11.0"
app="stern"
sudo mkdir -p /tools/${app}/
wget "https://github.com/wercker/stern/releases/download/${version}/${app}_linux_amd64" -O ${app}_${version}

sudo cp ${app}_${version} /tools/${app}/${app}_${version}
sudo chmod +x /tools/${app}/${app}_${version}
sudo ln -sfn /tools/${app}/${app}_${version} /usr/local/bin/${app}
```

## test: 
`stern -v`
---------------------------------

# kube-ps1

## Kubernetes prompt for bash and zsh
## link: 
https://github.com/jonmosco/kube-ps1

## instructions: follow documentation

---------------------------------

# kubectl-debug
## Debug your pod by a new container with every troubleshooting tools pre-installed
## link:

https://github.com/aylei/kubectl-debug

## instructions:
```
version="0.1.1"
app="kubectl-debug"
sudo mkdir -p /tools/${app}/
wget "https://github.com/aylei/kubectl-debug/releases/download/v${version}/${app}_${version}_linux_amd64.tar.gz" -O ${app}_${version}

sudo cp ${app}_${version} /tools/${app}/${app}_${version}
sudo chmod +x /tools/${app}/${app}_${version}
sudo ln -sfn /tools/${app}/${app}_${version} /usr/local/bin/${app}
```

---------------------------------

# visual studio Code
## extensions

Name: VSCode Dimmer Block
Id: imagio.vscode-dimmer-block
Description: Highlights the block containing the cursor, dims other text.
Version: 2.2.0
Publisher: imagio
VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=imagio.vscode-dimmer-block

Name: VSCode Essentials
Id: jabacchetta.vscode-essentials
Description: Turn VSCode into a supercharged IDE.
Version: 1.3.4
Publisher: jabacchetta
VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=jabacchetta.vscode-essentials




### to do
- Add krew to install plugins for kubectl
