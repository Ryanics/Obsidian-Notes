



When trying to set up github sync:

1. Set up github repo. It must be public. Need to make .gitignore file. 
2. Generate SSH keys if not generated previously: Go to ``.ssh``  and then type `ssh-keygen`
3. Set up SSH keys on github. Save the ssh key from `.ssh`, the file that ends in .pub. Not the other ssh file, because that is your private key. ONLY EVER USE A `.PUB`. 
4. Put the PUBLIC key into github under settings, SSH and GPG keys. 
5. Go to Obsidian. Press setting on the bottom right of the screen
6. Go to community plugins, enable. 
7. Find `github-sync by Kevin Chin` add it, enable. 
8. Click on github repo. Click code drop down, grab SSH key, put it into remote URL in the plugin. 
9. Enable all check boxes, `Check status on startup` and `Auto Sync on startup`, and setting the interval to `5` (meaning seconds.)
10. It should be set up now and ready to use. 