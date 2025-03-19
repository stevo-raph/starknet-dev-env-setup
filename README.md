# starknet-dev-env-setup
A step-by-step guide to setting up a Starknet development environment for those using Win 11 WSL2 Ubuntu 24.04

The Starknet Documentation is incomplete in that it does not provide instructions to setup a development environment ("dev env") for users of WSL2 Ubuntu (running on the Windows 11 platform). I found this also to be true of the content from the various Starknet Basecamp YouTube videos devoted to setting up the dev env. Following either of these guides can be confusing and frustrating because each fails to mention up front or at all the prerequisite necessity for either installing Docker Desktop and/or the Docker image "starknetfoundation-starknet-dev" [See: https://hub.docker.com/r/starknetfoundation/starknet-dev] and each thus ignores the specific commands one must navigate to successfully install a working Starknet dev env when using WSL2 Ubuntu. 

Hopefully, this Step-by-Step Guide will remove confusion and enable fellow WSL users to get to using the Starknet ecosystem faster.

* Step by Step to create Starknet project dev env using VSC & WSL Ubuntu 2404
**Assumptions: 
1.	You’ve installed Docker Desktop & pulled and run the starkwarefoundation/starknet-dev image. 
2.	You’ve installed the Dev Containers extension in VSC
3.	You’ve installed the Cairo 1.0 extension in VSC

Open VSC
Connect to WSL 24.04, open a new terminal
then mkdir xxxxx
then cd xxxxx
then code .  which opens a new terminal you’ll use henceforth
then New File from the Explorer and create a “.devcontainer.json” file
then once created, populate it with: 
	{ 
“name”: “dev”,
		“image”: “starknetfoundation/starknet-dev:latest”,
   "customizations":  {
        "vscode":  {
            "extensions":  [
                "StarkWare.cairo1",
                "tamasfe.even-better-toml" ] }}
}
then once .devcontainer.json is populated, click save, then enter ctrl/shift/P, and select “Dev Containers: Rebuild and Reopen in Container” 
(opens the project inside the Starknet container)
then scarb init – (select Starknet Foundry) which builds the project folders, files, dependencies
then scarb test
That’s it, you now have a Cairo/Starknet development setup.

