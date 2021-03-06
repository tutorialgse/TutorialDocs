Create a Website with RStudio: Setup
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

In this iteration we are going to proceed with the setup steps that you
will have to do before actually modifying and deploying your website.

## Install Required software

### R and Rstudio

In order to make your personal website you will first need to [install
R](https://cran.r-project.org/) for your operating system. YOu will also
need an installation of
[RStudio](https://www.rstudio.com/products/rstudio/).

You can follow the instructions in the following
[tutorial](https://campus.datacamp.com/courses/r-for-the-intimidated/introduction-to-course-and-rstudio?ex=3)

### Install git

Depending on your OS you will need to install
[git](https://git-scm.com/). YOu can follow the instructions in the
[following
page](https://www.datacamp.com/community/tutorials/git-setup):

### Hugo installation (OS dependent)

#### Windows

First install [Scoop](https://scoop.sh/). This is a package manager that
works similar to the package managers in Linux.

Access Windows
[Powershell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.1)
and type:

`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser iwr -useb get.scoop.sh | iex`

Reply yes to the question: **Do you want to change the execution
policy?**

Install Hugo and its dependencies by typing:

`scoop install git go hugo-extended`

#### MacOS

Open the **Terminal**

Install [Homebrew](https://brew.sh/), the Mac package manager, by
pasting the following command and pressing the Enter

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

update the repositories

`brew update && brew upgrade`

Install Hugo and its dependencies:

`brew install git golang hugo`

Open the hidden `~/.zshrc` (or `~/.bashrc`) file in a text editor, add
the following line, and restart your Terminal app so that Hugo can find
the location of its Go dependency.

`export PATH=$PATH:/usr/local/go/bin`

#### Linux

For Ubuntu based distributions

[Download](https://github.com/gohugoio/hugo/releases) the Hugo Extended
installer for Debian (hugo\_extended\_<VERSION>\_Linux-64bit.deb)

Open a terminal on the directory where you placed your installer and
type

`sudo dpkg -i <path_to_deb_file>/hugo_extended_<VERSION>_Linux-64bit.deb`

### Download a template

The provider [wowchemy](https://wowchemy.com/) has six different
[templates](https://wowchemy.com/templates/) you can use:

1.  [Academic/Resum??](https://academic-demo.netlify.app/)
2.  [Researcher](https://hugo-researcher.netlify.app/)
3.  [Research Group](https://research-group.netlify.app/)
4.  [Blog](https://hugo-blog-starter.netlify.app/)
5.  [Project Documentation](https://book-starter.netlify.app/)
6.  [Hello World](https://starter-hello-world.netlify.app/)

For this tutorial we are going to use the first.

To proceed go to the directory where you want to create your website
using your file explorer and open a terminal. If you are using WIndows
you should open a **power shell**. Now download the template by typing:

`git clone https://github.com/wowchemy/starter-academic.git`

Once you have cloned the repository, go to the location of the
repository on the file typing:

`cd <your-path>/starter-academic`

You can view the template by typing:

`hugo server`

If no errors are shown in the compilation you can paste the following on
the address bar of your web browser:

`http://localhost:1313/`

# Setting up R-studio

Stop the compilation by pressing `Crtl+c`. Then go to your website
folder by typing:

`cd <your-path>/starter-academic`

First you move the the `config.yaml` of your project to the root folder
by typing:

`mv ./config/_default/config.yaml .`

Now open RStudio and install the required package `blogdown`. Type the
following on the console.

`install.packages("blogdown")`

Then using RStudio GUI open the project:
`<your-path>/starter-academic/academic.Rproj`

To compile your site and preview it in RStudio type the following:

`blogdown:::serve_site()`
