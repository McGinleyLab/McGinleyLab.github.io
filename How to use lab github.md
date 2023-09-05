# How to use lab GitHub
## Repositories
- There are three ways you can work with the repositories (original) in the lab GitHub:
Fork, Copy code and Clone

1. Forking clones the repostiroy to create a new one, you work and update change to your forked repository but you can submit a push request to merge the change your make on the forked repository to the original one.
Use fork if the code is still under construction and you want to contribute to the development.

3. You can start a new repository in your GitHub and choose copy code to copy the repository at McGinleyLab.
This way you create an entirely independent repository for your own use.
It is recommended when you are simply using the code and need to make changes for your own project that do not need to share with the lab.

4. Simply clone the repository from McGinleyLab, you can freely use the code and modify them in your cloned repository or local machine.
But without authorization, you will get an error message when trying to push (upload) the changes for elsewhere to use.
The advantage of this method is easier to pull (download) updates from the original lab repository.

- You can alway use **git remote** function to change origin or add upstream for the repository.\
For expample, if you have premission to push the repository at McGinleyLab, it would be a good idea to still fork the repository to your own github,
clone the forked repo, then use:
	```
 	git remote add upstream git@respotiry_address (git@respotiry_address is the repository at McGinleyLab)
 	```
	This way you can work freely with your repository and push or pull the master repository (upstream) at McGinleyLab whenever needed, by using:
	```
 	git pull upstream main
 	git push upstream
 	```

## Credential
- You need a credential other then the account password to make change to the repository. There are serveral ways:
1. Install Git, which should come with the credential manager that can store the token for your account.

2. Install Git Desktop, which is the easiest way to work with repository on a local machine.

3. Generate token.\
Under account setting, go to *Developer settings--Personal access token--Tokens(Classic)* and generate a new token with/without expiration date.\
You need to keep this token as this is your password for modifying repository from now on until expired (well you can always generate a new one but not a good practice).

4. Generate SSH Key.\
SSH key has private and public part. GitHub uses the public key you submit to match with the local key on your computer to be able to recognize it.\
For server account or personal PC that belong to you, this is probably the best way and only way to use GitHub ssh clone.
- To generate the key:

	Linux:
	- Generate ssh key:
		``` 
	 	mkdir -p ~/.ssh
		ssh-keygen -t ed25519 -C "email used for GitHub"
		```
	
	- You can skip through the prompt asking for setting name and pass. Check if keys are now in the folder:
	 	```
	 	ls -al ~/.ssh
	  	```
	
	- There should be files named **ed25519** and **ed25519.pub** if you did not set the name yourself.\
	Next you need a ssh-agent to link the private key to your computer:
	 	```
	  	eval "$(ssh-agent -s)"
	  	ssh-add ~/.ssh/id_ed25519
	   	```

	Windows:
	- Add powershell folder to PATH
	
	- Set the sshd service to be started automatically
		```
		Get-Service -Name sshd | Set-Service -StartupType Automatic
		```
	
	- Start the sshd service
		```
		Start-Service sshd
		ssh-keygen -t ed25519
		```
	
	- By default the ssh-agent service is disabled. Configure it to start automatically.\
	Make sure you're running as an Administrator.
		```
		Get-Service ssh-agent | Set-Service -StartupType Automatic
		```
	
	- Start the service
		```
		Start-Service ssh-agent
		Get-Service ssh-agent
		```
	
	- Load your key files into ssh-agent
		```
		ssh-add $env:USERPROFILE\.ssh\id_ed25519
		```

- Open ed25519.pub and copy the key to GitHub under *Settings--SSH and GPG keys--New SSH key*\
Key type = Authentication Key

- Make sure to use ssh instead of https when cloning repository 
