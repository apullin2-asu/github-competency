# Git and GitHub for Beginners - Crash Course
Link: https://www.youtube.com/watch?v=RGOj5yH7evk

## Topic 1: What is Git
	- Git is a version control system that is free and open source.
	- Most widely used system today.
	- Version control is the management of changes to documents, computer programs, and other collections of information.
	- Helps us look back at all of our changes over time, so we can track down bugs or look at when we made a change.
	- CLI = Command Line Interface
	- Git is a good way to get started with command line.
	- A Git repository is the folder where your project is kept.
	- Git is the tool that tracks the changes in your code, GitHub is a website where you host all your Git repositories.
	- Each application or project is in a separate repository.

## Topic 2: Git Commands
	- clone [link from Github]: Bring a repository that is hosted somewhere like Github into a folder on your local machine.
	- add: Track your files and changes in Git (add it to being tracked)
	- commit: Save your files in Git
	- push: Upload Git commits to a remote repo, such as Gihub
		* -u: push upstream
	- pull: Download changes from a remote repo to your local machine, the opposite of push
	- init: Initializes an empty git in current folder.
	- status: Shows you current status of git commits.
	- branch: Shows you all the branches. The branch with a * is your current branch.
		* Hit q to exit this.
	- checkout: Use this to switch to a new branch.	
		* -b [name]: make a new branch to switch to named [name]
	- diff: Shows the difference between code branches.
	- reset: Either as is or with argument of [filename]. File is now no longer staged.
		* HEAD: pointer to last commit. With ~1, go to commit before last one. Unstages and uncommits.
		* Can do reset with hashcode as well to remove specific commit.
	- log: Shows list of all previous commits. Use spacebar to go down.

## Topic 3: Getting Started
	- Click plus button up top to make a new repository.
	- Give it a name and decide on settings if needed.
	- Once it has been made, you can either upload files from your computer or code directly in code editor in GitHub.
	- ReadMe is in almost every project, it include info on the project and what it does.
	- When you create a new file in online editor, you can give it a name in the top text bar.
	- The larger text box is for the code.
	- Commit will save the file to the project.
	- When you commit, you put in text for the subject and description of commit.
	- In markdown, use "#" to make some text bigger.
	- When you edit in the editor, now you are Updating and then you can save the commit as an update to the commit.
	- Click on [#] commits up top to look at all previous commits.
	- Each commit has a unique identifier.
	- When looking at previous commits, red and - means removed.  Green and + means added. White means stayed the same.
	- If it is on local machine:
		* If you have Mac or Linux, Git is likely already installed.
		* Type in "git --version" in CLI to get the version or find out if it is not installed.
	- When committing with command, -m "First text" is the subject and a second -m "Second Text" is the description.

## Topic 4: How to Connect Github Account to Local Machine
	- You connect your local machine to Github with a SSH key.
	- You first generate a key locally with this in CLI:  ssh-keygen -t rsa -b 4096 -C "[github email address]"
	- When you hit enter, it will generate a public/private rsa key pair and you will need to enter a file name for where to store this key.
	- Default file is in your .ssh directory/id_rsa
	- Then your key will be generated.
	- You can then search for your key and you want to use [keyname].pub
	- The other key is your private key, you do NOT want to share this with anyone.
	- Use cat [keyname].pub in CLI to see your key.
	- Copy this whole key. You can copy with terminal command pbcopy < ~/[keyname].pub and this will copy it to your clipboard.
	- In Github, go to SSH keys page and add a new key. Give it whatever title you want for easy reference.
	- Paste key you copied in the key box.
	- Now need to make sure your local git knows about this key.
	- Start your local ssh agent with eval "$(ssh-agent -s)"
	- Add your SSH private key to the ssh agent and store your passphrase in the keychain: 	ssh-add ~/.ssh/id_rsa

