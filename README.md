# This project is a simple HTML page with a few images as resources.

## This project is used to illustrate Bitbucket and Git concepts.

***

## Exercise

The goal of this exercise is to experience with undoing commits.


* Let's first use the recommended way: you have to revert the unwanted commit (last commit in the current history).


* After your revert, we should not have any `unwanted.txt` file in the repository, but we should have two commits in the history, after the `adding exercice's descritpion` one.


* Now you have to go back to the initial state: `git reset --hard HEAD~1`


* Try to reset the unwanted commit, using the non recommended (hard) way (hint, you just did id a second ago..).


* You should now have a clean directory (no `unwanted.txt`) and a clean history (no unwanted commit).


* What is the output of `git status`, is it normal ?



***

The images are free from rights illuminated texts from the French ["Bibliotheque Nationale"](http://www.enluminures.culture.fr/documentation/enlumine/fr/visites.htm) 