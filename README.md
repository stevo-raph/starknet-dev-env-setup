# Setting up a Starknet Development Environment on WSL2 Ubuntu with Docker

The Starknet documentation is incomplete when it comes to setting up a development environment (dev env) on WSL2 Ubuntu (running on Windows 11) using a Starknet Docker image and running a container from it. I also found the same gaps in the Starknet Basecamp YouTube *Fundamentals* videos.

Both guides can be confusing and frustrating because they fail to clearly mention — or even mention at all — the need to install Docker Desktop and/or the Docker image starknetfoundation-starknet-dev (Docker Hub link). As a result, they leave out the specific commands needed to set up a functional Starknet dev env on WSL2 Ubuntu.

This ***Step-by-Step Guide*** aims to fill those gaps, reduce confusion, and help fellow WSL2 users get up and running within the Starknet ecosystem more quickly.


**Assumptions: 
	1)	You’ve installed Docker Desktop & pulled and run the starkwarefoundation/starknet-dev image. 
	2)	You’ve installed the Dev Containers extension in VSC. 
	3)	You’ve installed the Cairo 1.0 extension in VSC.**

1. ***Open*** VSC
2. ***Connect*** to WSL 24.04, ***open*** a new terminal
3. then ***mkdir*** xxxxx
4. then ***cd*** xxxxx
5. then ***code .***  which opens a new terminal you’ll use henceforth
6. then ***New File*** from the Explorer and ***create*** a “**.devcontainer.json**” file
7. then once created, ***populate*** it by **typing** the following:

        {   
    "name": "dev",  
    "image": "starknetfoundation/starknet-dev:latest",  
    "customizations": {   
        "vscode": {   
            "extensions": [   
                "StarkWare.cairo1",   
                "tamasfe.even-better-toml"]   
                }     }     } 


So that it appears like this:

![Starknet devcontainer code](https://github.com/user-attachments/assets/02321a27-0c8b-4417-a6e0-900ec08070e9)

8. then once **.devcontainer.json** is populated, click ***save***, then ***press*** ctrl/shift/P, and ***select*** “Dev Containers: Rebuild and Reopen in Container” 
(opens the project inside the Starknet container)
9. then ***scarb init*** – (select Starknet Foundry) which builds the project folders, files, dependencies
10. then ***scarb test***

That’s it, you now have a Cairo/Starknet development setup ready for further Starknet-related activities. I've tested these instructions multiple times on multiple devices and it always produces the same successful outcome. But I also submitted this guide to the Starknet Discord server soliciting feedback from more experienced users. If someone there sees a problem with this guide, I'll update and notate immediately. 

**Notes:** It's not essential that Docker Desktop be installed because you can pull and run the Starknet image from the terminal. But, for me, I like to see the image inside Docker Desktop. 

I'll make no bones about this -- I am new to Starknet and Cairo. But, I'm learning quickly, and fumbling of course, but I consider this a necessary evil. So, I'll continue to post additional commentary and guides that I think might be useful to others facing a journey similar to mine. Next up, let's see how well documented is the process for deploying, declaring, and interacting with a Cairo smart contract on devnet first, then testnet.  One foot in front of the other!
