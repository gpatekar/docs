# Common git commands
<br />

###### Clone existing Repo
`git clone path`
<br />
<br />

###### Checkout
`git fetch origin`<b />
`git checkout -b branch-name origin/branch-name`
<br />
<br />

###### Stash
`git stash`<br/>

**Untracked files**
`git stash –include-untracked`<br/>

**Show all stash list**
`git stash list`<br/>

**Appl stash**
`git stash apply stash@{0}`<br/>

**Clear stash list**
`git stash clear`
<br />
<br />

###### Push local branch
`git push origin branch-name`<br />
 
**Push to different remote branch**
`git push origin local-name:remote-name`
<br />
<br />

###### Cache clean
`npm cache clean`
<br />
<br />

###### Amend
`git commit --amend --no-edit` (no-edit flag to commit without modifying message)
<br />
<br />

###### Cherry Pick
`git cherry-pick commit-id`
<br />
<br />

###### Rename Branch
**Local:**
`git branch -m old-name new-name`

**Remote:**
`git push origin :old-name new-name`
<br />
<br />

###### Discard changes
`git reset --hard`
<br />
<br />

###### Go to previous branch 
`git checkout -`
<br />
<br />

###### git config 
 `git config --global user.email "guru.patekar@gmail.com"`
