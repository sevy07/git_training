# Solution to **Git Advanced Training** exercises


***


## Exercise **working with several remotes** 

The goal of this exercise is to set up several remotes on the same repository, and share work between those remotes


* To start, clone this repository (if you haven't already done so), **we should be in your own personal fork**
  * `git clone <your_repository_url>`


* Declare a new remote : `main_repo` from the london fork `illuminated_texts_london`
  * `git remote add main_repo https://jchanal@rndwww.nce.amadeus.net/git/scm/stp/illuminated_texts_london.git`


* Fetch and checkout the newly created `test_remote_branch` branch from the main repository
  * `git fetch main_repo`
  * `git checkout --track main_repo/test_remote_branch`


* Push to a branch with another name on your own fork, set this newly created branch to trach your local branch
  * `git push origin test_remote_branch:my_own_test_remote_branch`
  * `git branch -u origin/my_own_test_remote_branch`


* Add as a new remote the person sitting next to you's fork
  * John Doe gave me read access to his illuminated_texts fork
  * `git remote add john_doe <john_doe_remote-url>`


* Ask him/her to create a branch, checkout this branch in local
  * John Doe created the branch `john_special_branch`
  * `git fetch john_doe`
  * `git checkout --track john_doe`


***


## Exercise **merge conflicts**

The goal of this exercise is to solve merge issues through an external merge tool.


* To trigger the merge conflict, merge the `dev branch` into this branch.
  * `git merge origin/dev`


* Get out of the merge conflicts.
  * `git merge --abort`


* Attempt to merge again.
  * `git merge origin/dev`


* This time resolve the merge issues by getting rid of the `merge_conflicts.jpg` images.
  * `git mergetool`
  * Resolve merge conflict using your preferred tool.

* Commit the result.
  * `git commit`

* Undo the merge by rewriting the history as if the merge never happened.
  * `git reset --hard HEAD~`

* Attempt to merge again, this time using `theirs`
  * `git merge origin/dev`
  * `git checkout --theirs illuminatedTexts.html`


* Commit and push the result in a `new branch` on your fork.
  * `git add illuminatedTexts,html`
  * `git commit`
  * `git push origin exercises/merge_conflicts:my_merge_conflict_resolution`


***


## Exercise **rebase example**

The goal of this exercise is to get familiar with the **rebase** functionality of Git

* Some changes have been committed on `dev branch` since we created our branch.
We are ready to deliver our feature branch, therefore we need to update it in order to get those changes


* Our team policy recommends a clean history strategy and therefore encourages a rebase instead of a merge


* Rebase your work with regards to `dev branch`
  * `git rebase origin/dev`
  * you enter a merge conflict state: `git mergetool` or `git checkout --theirs illuminatedTexts,html` followed by a `git add illuminatedTexts.html`
  * `git rebase --continue`


* Make sure the commits on `dev branch` are the same and that you did not modify any public commits
  * `git show HEAD^` should give the same result as `git show origin/dev` and it should be: `687e026 Merge pull request #32 in STP/illuminated_texts` 

* Inspect the commit with comment `setting up exercises's instructions` and compare its `$id` with the one of the person closest to you
  * `git log -S"setting up" --oneline` outputs: `64d9916 setting up exercises's instructions`

* Are they the same ? Is it normal ?
  * you will have a different commit id, but the same commit message, and the same commit content
  * it is normal : you applied the same commit, but with a different user id, at a different time, therefore the SHA-1 is different
  * this hilights one of the risk of rebasing, if we were to merge our branches, we would have a merge conflict.

  
***


## Exercise **interactive rebase**

The goal of this exercise is to get familiar with the **interactive rebase** functionality of Git

* I am working on my feature `interaqctive_rebase` I am done with my work and I am ready to deliver my feature.


* Our team policy recommends a clean history strategy and I have been scolded by my git maintainer due to the content of my pull request: `git log -4 --oneline` outputs
> `f85c7ba` adding file5

> `34975c2` creating file2

> `a66aa79` pushing files 3 and 4

> `b9d7a89` adding file1


* The goal is to have a clean history for my pull request:
> `75eb3a4` adding file4 and file5

> `fce7a7b` adding file2 and file3

> `b9d7a89` adding file1


* To do so you will have to use the **interactive rebase**
  * Our first commit is 4 commits back: to start rebasing we use `git rebase -i HEAD~4`


* Use a set of `pick`, `edit` `squash` and `reword` options to achieve a clean history
  * We do not want to modify the first commit : we use `pick` for the first one 
  * We need to change the order in order to pass the creation of file 2 after file 1: we move the corresponding commit so that it appears on second line.
  * We are not finished yet: we want to reword it, but also to add file 3, to do so we need the third commit: let's `reword` the second instead of pick and `edit` the next commit
  * For the last one, we want to combine it with the commit for file 4: let's use `squash`
  * You should end up with something like this:
  
> **pick** `b9d7a89` adding file1

> **reword** `34975c2` creating file2

> **edit** `a66aa79` pushing files 3 and 4

> **squash** `f85c7ba` adding file5

  * Save your changes
  
  
  * The script aplpies the first commit, then the second commit, and opens the editor to let you edit the commit message, let's edit it with:`adding file2`
  
  
  * The script now applies the third commit, and drops you in the command line, we want to edit the last commit, to add file3 to it :
  `git reset HEAD^`

  
  * Since we used the mixed mode, we have to add file3 to the staging area : `git add file3`


  * Then we amend the previous commit: `git commit --amend` we edit the commit message to have `adding file2 and file3`
  
  
  * We now have to add file4 since we only added file3 previously: `git add file4` and we commit: `git commit -m "adding file4"`
  
  
  * We can now resume the rebase operation : `git rebase --continue`

  
  * The script squashed the commit of file5 into our previous commit, and lets us edit the message, let's edit it to: `adding file4 and file5`

  
  * The rebase is now over, `git log --oneline -3` should give you the expected history, you can make sur that ech commit contains the correct files with `git show <commit_id>`
  

***


## Exercise **interactive staging**

The goal of this exercise is to get familiar with the **interactive staging** feature of GIT.

To do so, instead of having one single commit adding the whole solution, we want 3 commits:
1. One commit for `Peasants`
2. One commit for `Around the table`
3. One commit for `At War`


* Let's first revert to the previous commit, in order to edit it: `git reset HEAD~`


* Let's start the interactive staging script: `git add -i`


* Commit your work in order to have the desired history  
  * you want to pick hunks of lines to add them to the index: choose `patch`
  * choose illuminatedtexts.html: `1`
  * confirm: `<enter>`
  * `Peasants` corresponds exactly to the first hunk: `y`
  * You have enough for your first commit: `q`
  * Let's quit the script: `q`
  * Let's commit: `git commit -m "adding Peasants"`

  
* Repeat previous commands for the following 2 hunks


***

## Exercise **creating a hook**

The goal of this exercise is to get familiar with GIT Hooks, and create your own hook


* To start, get the file `prepare-commit-msg.toEdit` and copy its content in your `prepare-commit-msg` file in your `.git\hooks` directory
  * You can find the solution script in the following file: `prepare-commit-msg.solution`
  * It needs Python v2 to run


***


## Exercise **clean and smudge filters**

The goal of this exercise is to get familiar with the **filter** feature of Git

* Have a look at your `.gitattributes` file : you can see that we have defined a filter for all `*.config` files: `*.config  filter=hide_credentials`


* You have to define this filter in your config:
  * run `git config filter.hide_credentials.clean "~/scripts/.clean" `
  * run `git config filter.hide_credentials.smudge "~/scripts/.smudge" `


* You have to move the `.clean` and `.smudge` scripts to the correct place: in `%HOME%/scripts`


* You are good to go:
  * Let's trigger the **smudge** filter: delete `connection.config`, and then undo this deletion. What heppened to your file ?
  * Let's trigger the **clean** filter: add a line at the bottom of `connection.config`, commit and push: you will see that the user and password are not pushed.
  * You will need perl accessible for it to work


* Modify just the password and/or the user, and commit. What happened to your commit ?
  * When you are about to commit, your file goes through the `clean` filter, which cleans your changes. Git sees that there are no changes, and ignores your commit