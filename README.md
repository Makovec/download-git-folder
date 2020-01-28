# download-git-folder

Yesterday I saw some article regarding ARM templates tests. There is a script for it but as it is a part of [Azure Quick start templates](https://github.com/Azure/azure-quickstart-templates) (QST), you need to download whole repository to get just a few files. So I decided to create this script which is able to download any part (folder) from any GitHub repository.

**Note:** I use variable `$GitApiKey` in my profile. This API key is used to access GitHub API to get the files. If you do not have API key created, you can easily [create one](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line#creating-a-token). As a permission is enought to set *public_repo*.

When you have a token, you have two ways:

1. Set global variable named **GitApiKey**. Then you can run the script without any changes.
2. Change the line containing *Authorization* header. Either add your token directly or add some script variable and reference it there, like `'Authorization' = "token $yourApi"`.

## Usage

### Example 1

No parameters, just run it. It will download this repo to folder `git-out`.

```powershell
>_ .\Get-GitRepo.ps1 -Verbose
VERBOSE: Created folder C:\repo\download-git-folder\git-out
VERBOSE: File: https://raw.githubusercontent.com/Makovec/download-git-folder/master/README.md
```

### Example 2

Download example folder from Azure QST to given folder (myTTK).

```powershell
>_ .\Get-GitRepo.ps1 -Owner Azure -Repo azure-quickstart-templates -Path test/arm-ttk -RootFolderName myTTK

>_ tree .\myTTK
C:\REPO\DOWNLOAD-GIT-FOLDER\MYTTK
├───cache
└───testcases
    ├───CreateUIDefinition
    └───deploymentTemplate
```

