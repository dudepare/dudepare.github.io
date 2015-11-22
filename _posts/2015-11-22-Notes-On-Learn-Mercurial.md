---
layout: post
---

My goal today is [learn Mercurial](https://www.mercurial-scm.org/wiki/TutorialClone). 

`hg summary`

see which revision is currently checked out.

`hg clone src dest`

*src* can be a url or a local folder.
*dest* is optional. when you don't specify a dest, it will create a folder with the same name. if you specified a local folder it will 
create that folder.

`hg [parameters] tip`

same as hg log -r tip

*parameters*
-q          quiet. will only show the revision number of the tip. nothing more.


`hg log [parameters]`

to view the history of the repository. 
view all the commits, merges, etc.

*parameters*
-v          for a more detailed output(means verbose)
--debug     shows all details
--graph     shows an ASCII graph of the history of the repository
-r[number]  show specific changeset details, number is the changeset number
-r tip      show the latest commit
-p          to see the changes made

`hg diff`

shows the differences in the tip vs the modified version of the repository

`hg revert [file] or [--all]`

restores the original version of the file prior to modification.
saves the modified version in a separate file <filename>.orig

*parameters*

--all       will revert all the changes across all files

`hg parent`

i yet don't understand what this command does.
let's give it time to expose itself to us.

`hg pull`

first you cd in to the destination directory.
perform an *hg pull [source directory]*
changesets that are not in the destination directory are copied from the source directory
possibly when source dir and dest dir have both changes, hg pull could add another head to the destination directory/repository.

`hg heads`

view two different heads in the repository

`hg annotate [filename]`

shows the changeset information per file line. I'm thinking is this like the blame command?

`hg export [revision number] or [changeset id] or tip` > file.diff

a way to create a diff/patch file to be shared or tucked away for code review.

`hg resolve -m [filename]`

tell mercurial you have successfully resolved the conflict in [filename]

