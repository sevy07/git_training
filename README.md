# This project is a simple HTML page with a few images as resources.

## This project is used to illustrate Bitbucket and Git concepts.

***

## Exercise

The goal of this exercise is to get familiar with the **filter** feature of Git

* This exercise assumes that you have `perl` installed on your machine.

  Run `perl --version` to make sure it is the case. If it is not, Perl can be found [here](http://www.perl.org/)
  

* Have a look at your `.gitattributes` file : you can see that we have defined a filter for all `*.config` files: `*.config  filter=hide_credentials`


* You have to define this filter in your config:
  * run `git config filter.hide_credentials.clean "~/scripts/.clean" `
  * run `git config filter.hide_credentials.smudge "~/scripts/.smudge" `


* You have to move the `.clean` and `.smudge` scripts to the correct place: in `%HOME%/scripts`

  You will have to create a `scripts` directory in your HOME path, as it most likely does not exist, and put both scripts there.


* You are good to go:
  * Let's trigger the **smudge** filter: delete `connection.config`, and then undo this deletion. What heppened to your file ?
  * Let's trigger the **clean** filter: add a line at the bottom of `connection.config`, commit and push: you will see that the user and password are not pushed.


* Modify just the password and/or the user, and commit. What happened to your commit ?


***

The images are free from rights illuminated texts from the French ["Bibliotheque Nationale"](http://www.enluminures.culture.fr/documentation/enlumine/fr/visites.htm) 
 