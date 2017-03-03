# Solution to **Git basics Training** exercises


***


## Exercise **basics/first steps** 

The goal of this exercise is to order the illuminated texts between 3 groups by editing the html file.


* Modify the `illuminatedTexts.html` file in order to associate each city with its corresponding image
  * eg. Besancon with Besacon, Chateauroux with Chateauroux, etc...


* Once you are happy with your changes, add the changes to the staging area.
  * `git add illuminatedTexts.html`


* Commit, and push.
  * `git commit -m "US-1 sorting the images"`
  * `git push`


* Create a pull request to the main repository, to incorporate your changes.
  * Click on `Create pull request` button
  * Choose `Stash Training Project / illuminated_texts_london`

***


## Exercise **basics/merge_conflicts** 

The goal of this exercise is to solve merge issues through an external merge tool.


* To trigger the merge conflict, merge the `dev` branch into this branch.
  * `git merge origin dev`
  
* Get out of the merge conflicts.
  * `git merge --abort`
  
* Attempt to merge again.
  * `git merge origin dev`

* This time resolve the merge issues by getting rid of the `merge_conflicts.jpg` images.
  * `git mergetool`

* Commit the result.
  * `git commit -m "US-1 merge conflicts resolved"`

***


## Exercise **basics/modifying_last_commit_comment** 

The goal of this exercise is to modify the comment of the last commit.


* Modify the comment of the last commit to have a proper comment, and no longer `this is a wrong comment`
  * `git commit --amend -m "adding new file"`

***


## Exercise **basics/undoing_commits** 


The goal of this exercise is to experience with undoing commits.


* Let's first use the recommended way: you have to revert the unwanted commit (last commit in the current history).
  * `git revert HEAD` or `git revert 469cd8e43ac`

* After your revert, we should not have any `unwanted.txt` file in the repository, but we should have two commits in the history, after the `adding exercice's descritpion` one.
  * `git log -3 --oneline` shows 3 commits: `<your  revert commit>`, `469cd8e43ac`, and `789cbd50891`


* Now you have to go back to the initial state: `git reset --hard HEAD~1`
  * `git reset --hard HEAD~1`
  * now `git log -2 --oneline` shows 2 commits: `469cd8e43ac`, and `789cbd50891`


* Try to reset the unwanted commit, using the non recommended (hard) way (hint, you just did id a second ago..).
  * `git reset --hard HEAD~1`
  * `git log -2 --oneline` shows 2 commits: `789cbd50891`, and `277031b5875`, `469cd8e43ac` has disappeared

* You should now have a clean directory (no `unwanted.txt`) and a clean history (no unwanted commit).
  * it should be the case

* What is the output of `git status`, is it normal ?
  * `git status` should tell you: `Your branch is behind 'origin/exercises/basics/undoing_commits' by 1 commit, and can be fast-forwarded.`
  * This is normal: `469cd8e43ac` has disappeared from your local history, but it is still present on the server
  * To solve this, you need to perform a `git push -f`

***



## Exercise **basics/cherry-picking** 

The goal of this exercise is to get familiar with the cherry-picking functionality of git.


* Cherry-pick the commit with comment `very urgent fix` from branch `cherry-pick`
  * `git cherry-pick 4c5f42b7fb9`


***

The images are free from rights illuminated texts from the French ["Bibliotheque Nationale"](http://www.enluminures.culture.fr/documentation/enlumine/fr/visites.htm) 