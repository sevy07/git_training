# This project is a simple HTML page with a few images as resources.

## This project is used to illustrate Bitbucket and Git concepts.

***

## Exercise

The goal of this exercise is to find the **first** commit that introduced an issue **without even looking into the code!**


* To start, use `git bisect start`


* Opening `illuminatedTexts.html` in your browser you should see an error blinking: that's the bug.


* Since the bug is present in the current commit, flag it as bad: `git bisect bad`


* Find a commit that was good, and flag it as good (hint, it is the last commit on master branch..):

  `git bisect good <commit_id>`


* Git will now move HEAD from commit to commit, asking you if the bug is present or not.

  If the bug is present, enter `git bisect bad` if the bug is not present, enter `git bisect good`


* Continue until the faulty commit is identified, which commit is it ? run `git show <faulty_commit_id>` to inspect it


* Finish by using `git bisect reset`



***

The images are free from rights illuminated texts from the French ["Bibliotheque Nationale"](http://www.enluminures.culture.fr/documentation/enlumine/fr/visites.htm) 