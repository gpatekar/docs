# Common git commands


###### Clone existing Repo
git clone path



###### Checkout
git checkout -b branch-name origin/branch-name



###### Stash
git stash
git stash list
git stash apply stash@{0}



###### Push local branch to different remote branch
git push origin local-name:remote-name



###### Cache clean
npm cache clean



###### Amend
git commit --amend --no-edit (no-edit flag to commit without modifying message)



###### Cherry Pick
git cherry-pick commit-id



###### Rename Branch
**Local:**
git branch -m old-name new-name

**Remote:**
git push origin :old-name new-name



###### Discard changes###### The
git reset --hard

###### Go to previous branch 
git checkout -



###### git config 
 git config --global user.email "gurudatta.patekar@creativecapsule.com"
