# Azure Infrastructure Development Setup Scripts (Windows)
Repo containing installation scripts for your Azure infrastructure development workstation.

## Authors

- Kevin Evans - GitHub: @kevinevans1 - Twitter: https://twitter.com/thekevinevans

## Brief
This repo aids folks walking along the StreamingClouds episode "Azure IaC development workstation setup"

- StreamingClouds YouTube Episode  https://www.youtube.com/watch?v=C7I6EseqWyM 

These script's will install dependencies for getting you up and running with deploying Infrastructure as Code into Azure using Windows Subsystem for Linux,Terraform,Bicep,Powershell and Azure CLI.

### Operating System Requirements 
- Windows 11 Version 21H2(OS Build 22000.795) or higher
- CPU Virtualization Enabled

### Package Managers
- Chocolatey https://chocolatey.org/install
- Homebrew https://docs.brew.sh/Homebrew-on-Linux
- APT https://help.ubuntu.com/community/AptGet/Howto 

## Chocolatey Packages (Windows Desktop)
- notepad ++ https://notepad-plus-plus.org/
- git https://git-scm.com/
- VScode https://code.visualstudio.com/
- Powershell core 7 https://github.com/PowerShell/PowerShell
- Azure CLI https://docs.microsoft.com/en-us/cli/azure/install-azure-cli

## Homebrew Packages (WSL Ubuntu)
- Azure CLI https://docs.microsoft.com/en-us/cli/azure/install-azure-cli
- Terraform https://www.terraform.io/downloads
- Azure Terrafy https://github.com/Azure/aztfy 

## APT (WSL Ubuntu)
- Powershell core 7 https://github.com/PowerShell/PowerShell 



### Windows Subsystem For Linux

## Installation Steps

1. To start, we will need to enable the Virtual Machine Platform module and Windows Subsystem for Linux feature. Open up your Start menu and locate the Turn Windows features on or off menu. (Make sure you have CPU virtualization enabled in the BIOS)

![Azure Windows Workstation](/assets/img/pic1.png)

2. Next, find the Virtual Machine Platform and Windows Subsystem for Linux options. Check both of these boxes and then press OK to enable the features.

![Azure Windows Workstation](/assets/img/pic2.png)

3. Windows will make the changes, which may take a minute or two, then ask you to restart your system for the changes to take effect. Proceed with the reboot.

4. Navigate to the Windows Terminal and run the following commands to download the latest WSL 2 Kernel.

```
wsl --shutdown
```
```
wsl --update
```
Once completed reboot.

5. When your system boots back up, go to your Start menu and find the Microsoft Store. Once there, search for Ubuntu 22.04.

6. Once you have located the Ubuntu 22.04 LTS page, click on the “Get” button to download it.

- Ubuntu 22.04 LTS Microsoft Store Download (https://www.microsoft.com/store/productId/9PN20MSR04DW)

![Azure Windows Workstation](/assets/img/pic3.png)

7. Once the download is complete, you can open Ubuntu 22.04 from your Start menu.

8. There will be an installation process that appears, and it should not take very long. The distro will be unpacked and ready to use shortly.

![Azure Windows Workstation](/assets/img/pic4.png)

9. At this time, you will also be asked to create a new user account for Ubuntu 22.04 and some other small configuration settings.

![Azure Windows Workstation](/assets/img/pic6.png)

10. All done. You can now open Ubuntu 22.04 from your Start menu any time you want to use it. You will be presented with a command line terminal and can execute nearly all the same commands you could on a local Ubuntu 22.04 machine.

![Azure Windows Workstation](/assets/img/pic7.png)


## Chocolatey Packages (Windows Desktop)
1. Navigate to the Windows Terminal (Run as administrator)
- Install Chocolatey 
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
Close the terminal and reload under Administrator again.

2. Install the following choco packages
```
choco install notepadplusplus.install -y 
choco install git.install -y 
choco install vscode -y 
choco install powershell-core -y
```

## WSL Installation Packages (Ubuntu)
1. Navigate to Ubuntu shell using Windows Terminal
- Install Homebrew package manager, by running these commands under sudo
```
sudo apt install curl
```
```
sudo apt install git
```
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. Once the Homebrew installation is complete run the following commands to add Homebrew to your local user path and install Homebrew's local dependencies:
```
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/<yourusername>/.profile
```
```
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```
```
sudo apt-get install build-essential
```

## Install IaC Deployment Tools
1. From your Ubuntu terminal run the following commands to install Azure CLI,Terraform,Azure Terrafy using Homebrew.
```
brew update && brew install azure-cli
brew update && brew install terraform
brew update && brew install aztfy
```
2. Install Bicep from the Azure CLI
```
az bicep install
```

3. Install PowerShell 7 (Optional)
- Update the list of packages
```
sudo apt-get update
```
- Install pre-requisite packages.
```
sudo apt-get install -y wget apt-transport-https software-properties-common
```
- Download the Microsoft repository GPG keys
```
wget -q "https://packages.microsoft.com/config/ubuntu/$(lsb_release -rs)/packages-microsoft-prod.deb"
```
- Register the Microsoft repository GPG keys
```
sudo dpkg -i packages-microsoft-prod.deb
```
- Update the list of packages after we added packages.microsoft.com
```
sudo apt-get update
```
- Install PowerShell
```
sudo apt-get install -y powershell
```
- Start PowerShell
```
pwsh
```








## Git Quick Config (Run from Windows Terminal)
When you make commits on your local system and push them to GitHub or Azure DevOps, the commit meta data determines which account name to attach to the push.

To ensure your commits in GitHub/Azure DevOps appear with your user account, configure the below conditions to get get you up and running:

To set your global username/email configuration:
Open the command line.

Set your username:
```
git config --global user.name "FIRST_NAME LAST_NAME" 
```

Set your email address:
```
git config --global user.email "MY_NAME@example.com"
```


## VSCode Extension List
1. WSL Extension's
- WSL VSCode Site (https://code.visualstudio.com/docs/remote/wsl)
- Remote Development Extension Pack (https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

2. Prettier Code formatter
- Prettier (https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

3. Spell Checker
- Code Spell Checker (https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)

4. Bicep Authoring Extension
- Bicep (https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep)

5. Terraform Authoring Extension
- Terraform (https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform)

## Feedback
Please report any bugs via issues here on GitHub and I will look to fix, or try and fix yourself and submit a pull request :)

Thanks

Kevin





