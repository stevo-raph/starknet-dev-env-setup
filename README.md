# starknet-dev-env-setup
The Starknet documentation is incomplete when it comes to setting up a development environment (dev env) on WSL2 Ubuntu (running on Windows 11). I also found the same gaps in the Starknet Basecamp YouTube videos covering dev env setup.

Both guides can be confusing and frustrating because they fail to clearly mention — or even mention at all — the need to install Docker Desktop and/or the Docker image starknetfoundation-starknet-dev (Docker Hub link). As a result, they leave out the specific commands needed to set up a functional Starknet dev env on WSL2 Ubuntu.

This Step-by-Step Guide aims to fill those gaps, reduce confusion, and help fellow WSL2 users get up and running with Starknet more quickly.

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

