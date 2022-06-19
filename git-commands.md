# Common git commands
<br />

###### Clone existing Repo
git clone path
<br />
<br />

###### Checkout
git checkout -b branch-name origin/branch-name
<br />
<br />

###### Stash
git stash
git stash list
git stash apply stash@{0}
<br />
<br />

###### Push local branch to different remote branch
git push origin local-name:remote-name
<br />
<br />

###### Cache clean
npm cache clean
<br />
<br />

###### Amend
git commit --amend --no-edit (no-edit flag to commit without modifying message)
<br />
<br />

###### Cherry Pick
git cherry-pick commit-id
<br />
<br />

###### Rename Branch
**Local:**
git branch -m old-name new-name

**Remote:**
git push origin :old-name new-name
<br />
<br />

###### Discard changes
git reset --hard
<br />
<br />

###### Go to previous branch 
git checkout -
<br />
<br />

###### git config 
 git config --global user.email "gurudatta.patekar@creativecapsule.com"
