# This project is a simple HTML page with a few images as resources.

## This project is used to illustrate Bitbucket and Git concepts.

***

## Exercise

The goal of this exercise is to get familiar with the **interactive rebase** functionality of Git, and most particularly with the **edit** fetaures

* I am working on my feature `interactive_rebase_edit` I am done with my work and I am ready to deliver my feature, but I just noticed I forgot a file in a previous commit!


* Our team policy recommends a clean history strategy and I have been scolded by my git maintainer due to the content of my pull request: **there is no file2 in the 2nd commit**, I forgot it :S


 `git log -3 --oneline` outputs

> `f85c7ba` adding file3

> `a66aa79` adding file1 and file2

> `b9d7a89` setting up exercise's instructions 

* The goal is to have a clean history for my pull request:

> `75eb3a4` adding file3

> `fce7a7b` adding file1 and file2

> `b9d7a89` setting up exercise's instructions


* To do so you will have to use the **interactive rebase**


* You will have to create a dummy `file2.txt` to add to commit `a66aa79`


* Use a set of `pick` and `edit` options to achieve a clean history in your pull request towards `master`


***

The images are free from rights illuminated texts from the French ["Bibliotheque Nationale"](http://www.enluminures.culture.fr/documentation/enlumine/fr/visites.htm) 