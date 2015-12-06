# Git Auto-Merge Messages (Internal)
3 mins

## Overview
You may do a `git pull` and **end up stuck in a text editor!**.  
Here's why, and how to get out of it.

If you:
- `git pull` changes, **and**
- the remote (GitHub) has new changes, **and**
- the local (your machine) also has new changes, **and**
- the changes in the remote and the local versions are automatically mergeable, **then**

Git will merge both versions into a new version, stage the new version, and generate an auto commit message.
Git will open the automatic commit message in the default Git text editor. You don't need to add anything. 
<br>
Closing the file will trigger the commit with the merge to be executed, which is what we want.
**Close the file** - If the default editor is nano, close the file with 'ctrl+x'. If the default editor is sublime, 'cmd+w'[OSX], 'ctrl+w'[Linux/Windows]


## Topics Covered / Key words:
- auto merge
- stuck in a text editor


## Type:
- Article

