Create a Website with RStudio: Deploy your website
================

This is the first part of the tutorial to create a website using
[Hugo](https://gohugo.io/) and [RStudio](https://www.rstudio.com). We
are going to use a particular flavor of Hugo templates called
[Wowchemy](https://wowchemy.com/) (previosuly know as academic Hugo).

With Wowchemy, the default option is to deploy the site using a
subscription based service called [Netlify](https://www.netlify.com/).
The process is very well explained on their
[documentation](https://wowchemy.com/docs/getting-started/install/).

As advocates for free technology we are going to opt for a second way to
modify and deploy your website using your own PC and [Github
Pages](https://pages.github.com/).

In this iteration we are going to proceed with the some of the most
basic and common ways to modify your website.

## Setting up github

First you will need to [log-in](https://github.com/login) or [create a
github account](https://github.com/join)

Next you will need to create an empty repository where you are going to
save your local files from the website build. A detailed set on
instructions to this is can be fund [this
link](https://docs.github.com/en/github/importing-your-projects-to-github/adding-an-existing-project-to-github-using-the-command-line)

Once the **empty** repo is created, with any name you like, for example
**tutorial\_gs**, we are ready to copy the contents of your website to
the repo.

1.  First connect your local repository to the github repo.

    -   Open a terminal and navigate to the site of your website:
        `cd <your-path>/starter-academic`
    -   connect to the repo with the online repo by typing:
        `git remote set-url origin <YOUR_REPO_URL>.git` For Example
        `git remote set-url origin https://github.com/tutorialgse/tutorial_gs.git`
    -   To verify the origin type: `git remote -v`

2.  Next you have to commit the changes you have made

    -   For this your global `user.name` and `user.email` should be
        configured already on your machine. You can check if that is the
        case with: `git config --list --show-origin`
    -   if not set yet, you can use :
        `git config --global user.name "John Doe"`
        `git config --global user.email johndoe@example.com`
    -   then add all the changes made to your repo by typing:
        `git add .`
    -   Now commit all the changes:
        `git commit -m "First commit on the web"`
    -   Push your repo to your new empty repo typing
        `git push origin master` you will be asked for your credentials
        after this

Now we are going to create the second repo to host the page. For this to
work you have to name the repo as follows `<USERNAME>.github.io`. Where
`<USERNAME>` is the user name that you chose for your account. We will
save the generated site to this repository.

In your `./config/_default/config.yaml` file, set
`baseurl = "https://<USERNAME>.github.io/"`

Next remove the directory `./public`.

We are going to create the submodule to populate our website deployment
repository

`git submodule add -f -b master https://github.com/<USERNAME>/<USERNAME>.github.io.git public`

## Deploy your site

Generate the website again by typing on the console:

    hugo
    cd publi
    git add .
    git commit -m "Build website"
    git push origin master
    cd ..

After this, go to `"https://<USERNAME>.github.io/"` and you should be
able to see your website.

## Updating your site

To update your websites make your modifications as per the second
tutorial. Then add and commit your changes

    cd <your-path>/starter-academic
    git add .
    git commit -m "update your website" 
    git push origin master

After that re-generate the website by typing:

`hugo`

When the process is done, proceed to the `public/` directory, then add,
commit and push all changes.

    cd <your-path>/starter-academic/public
    git add .
    git commit -m "update your website web repo" 
    git push origin master

After this, go to `"https://<USERNAME>.github.io/"`, after a couple of
minutes you should be able to see your website updated.
