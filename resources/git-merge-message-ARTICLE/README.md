# Git Auto-Merge Messages (Internal)
3 mins

## Overview
You may do a `git pull` and **end up stuck in a text editor!**.  
Here's why, and how to get out of it. 

If you:
- `git pull` changes, and 
- the remote (GitHub) has new changes, and
- the local (your machine) has new changes, and
- the changes in the remote and the local versions are automatically mergeable, then

Git will merge both versions into a new version, stage the new version, and generate an auto commit message.
To check if there is anything you want to add to the message, Git will open the commit message in whatever the default Git text editor is.  
Normally, there's nothing you need to add.  
Closing the file will trigger the commit with the merge to be executed, which is what we want.
If the default editor is nano, close the file with 'ctrl+x'. If the default editor is sublime, simply close the file


## Topics Covered / Key words:
- auto merge
- stuck in a text editor


## Type:
- Article

