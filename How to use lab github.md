# How to use lab GitHub
## Repositories
- There are three ways you should work with the repositories (original) in the lab GitHub:
Fork, Copy code or change origin, Clone

1. Forking clones the repostiroy to create a new one, but you can use pull request to merge the change you make to the original repository.
Use fork if you think the change you made to the code may be needed for other lab members.

2. You can create a repository in your GitHub and choose copy code to copy the original repository.
This way you create a totally independent repository for your won use and you can pull anytime to update the change you made.
It is recommended when you are simply using the code and need to make changes for your own project which do not need to share with the lab.
You can also clone the respository and made the cloned one the origin and the original repository the upstream. 
This way you can pull configuration change to your own origin repository, and send pull request to the upstream when the original files need to be modified.

3. When cloning the repository, you can freely use the code and modify them in your cloned repository or local machine.
But without authorization, you will get an error message when trying to pull (upload) the changes for elsewhere to use.

## Credential
- You need a credential other than the account password to make change to the repository. There are serveral ways:
1. Install Git, which should come with the credential manager that can store the token for your account.

2. Install Git Desktop, which is the easiest way to work with repository on a local machine.

3. Generate token.
Under account setting, go to Developer settings--Personal access token--Tokens(Classic) and generate a new token with/without expiration date.
You need to keep this token as this is your password for modifying repository from now on.

4. SSH Key.
SSH key has private and public part. It allows GitHub to recognize your computer with the public key. To generate it:
Linux:
	'''
	mkdir -p ~/.ssh
	ssh-keygen -t ed25519 -C "email used for GitHub"
	'''
You can enter through the prompt asking for setting name and pass.
	'''
	ls -al ~/.ssh
	'''
There should be files named ed25519 and ed25519.pub if you did not set the name yourself
	'''
	eval "$(ssh-agent -s)"
	ssh-add ~/.ssh/id_ed25519
	'''

Windows:
MS
Add powershell folder to PATH

- Set the sshd service to be started automatically
'''
Get-Service -Name sshd | Set-Service -StartupType Automatic
'''

- Start the sshd service
'''
Start-Service sshd
ssh-keygen -t ed25519
'''

- By default the ssh-agent service is disabled. Configure it to start automatically.\
Make sure you're running as an Administrator.
'''
Get-Service ssh-agent | Set-Service -StartupType Automatic
'''

- Start the service
'''
Start-Service ssh-agent
Get-Service ssh-agent
'''

- Load your key files into ssh-agent
'''
ssh-add $env:USERPROFILE\.ssh\id_ed25519
'''

Open ed25519.pub and copy the key to GitHub under Settings--SSH and GPG keys--New SSH key
Key type = Authentication Key
 