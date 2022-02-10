README
================
jsg
8/25/2020

## Getting started

At this point I’m assuming you received an invitation to view an
assignment on github classroom and accepted it. You now have a private
repository of these files. This repository contains starter code for all
assignments.

### If you are using RStudio that you installed on your personal device

To start working on an assignment, open RStudio on your computer

![Screenshot showing where to start creating a
repository](https://lh3.googleusercontent.com/pw/ACtC-3ddyHNvzmRICUa_CmWQmzbz5jr9aTdo_bs9yH9ZbfUPe2LjS46TYj1FsD7CjhKL3rknFZkui-YecWokRGY03cj8occR5HJN56P5N8KJTCUPgciKCAwD8YHJEKXXOOjH-LI8k1G8p88MGB7d_6ov4EJtQQ=w879-h664-no)

Select file, new project, Version control. On the next screen select
git. If this isn’t available, you may need to install git (free) on your
system. You can download it at <https://git-scm.com/download/>.

Next you’ll need to enter the url for your repository. Open a browser,
go to <https://github.com/> and sign in to your account. Look under your
repositories for the correct one and open it. An easy place to see all
repositories (including those from github classroom) is
<https://github.com/settings/repositories>.  
Then look for the Code button (usually green) in the githbub repository
(where you may be reading this…).

![Click the green code button to get the repository
url](https://lh3.googleusercontent.com/pw/ACtC-3c6iXUxY_YkEQktN9szfL0Jfl3-jJnjfp2dwbMU_NtnOtoCOFzJcpRN1r0X0zCZlH2gtB9JlXz7_WLgXMBAU7a2K_vwTX5taNBBWwSgsO558aqLZEtKmH_cMpwv7ukzYi7R4ffncWbcscAy8sAzBcZ4Ww=w692-h490-no?authuser=0)

Click it, then copy the web url (or click the copy icon). Input that
into the Rstudio Repository URL space. Then name the project (maybe
Assignment 1,2, etc?). The Create project… field can be left blank to
just save all projects into the main directory. Alternatively you can
click Browse and make an Assignments folder if you want. Whatever you
choose, the project will be saved in new folder in that location using
the name you chose. As of Fall 2021, Github no longer accepts usernames
and passwords for authentication. However, Rstudio may ask you for these
depending on what version you are using. Don’t be surprised if you enter
your password correctly but your attempt to create a repository (or push
commits to it) still fails because you need to setup or reset a token.

![If you see this, it means you need to setup or reauthorize a github
token](https://lh3.googleusercontent.com/pw/AM-JKLW24QFJWE5drC-dx2ldqcUZtNvtC-zl6HIiQLUoRYcy9enZV1eomlHk3afwzU_uiythMdAZlKi2eY_nlmdBgpcWcxK5qcZWPnufblrmUYb2bB4YOqBpEQaRqRpQWEX86lRACZFIe2OjFmZYwT30_fYjxA=w704-h296-no?authuser=0)

If you see this message now, go to the **Github 2-factor authentication
(required as of Fall 2021)** section!). If not, you can continue, but
note you’ll have to do it later (when you push changes).

Go to the next section (**Now we can actually work in R**) to get
started

### If you are using Rstudio cloud…

You’ll instead see something like this:

![In Rstudio cloud, click new project to start a
repository](https://lh3.googleusercontent.com/pw/ACtC-3dVAm8XnMQH9ebnayG0SgBgSewlPFWyJmubIbASefCQ0NKiuZHsQO6eUbzy-Y0LZ6U7KbPkmHCi91tJ4lm7xPs4xf0A3fyMXyMKuzfJ6B2tADIq_NX9GmYRrZS5OuZ6Y1DcCxyzMmmEsV-_DyV9XrLLJA=w1320-h581-no?authuser=0)

To start working on an assignment, select **New Project**, **New Project
from Github repo**, then enter the url for your repository. Open a
browser, go to <https://github.com/> and sign in to your account. Look
under your repositories for the correct one and open it. An easy place
to see all repositories (including those from github classroom) is
<https://github.com/settings/repositories>.  
Then look for the Code button (usually green) in the githbub repository
(where you may be reading this…).

![Click the green code button to get the repository
url](https://lh3.googleusercontent.com/pw/ACtC-3c6iXUxY_YkEQktN9szfL0Jfl3-jJnjfp2dwbMU_NtnOtoCOFzJcpRN1r0X0zCZlH2gtB9JlXz7_WLgXMBAU7a2K_vwTX5taNBBWwSgsO558aqLZEtKmH_cMpwv7ukzYi7R4ffncWbcscAy8sAzBcZ4Ww=w692-h490-no?authuser=0)

Click it, then copy the web url (or click the copy icon). Input that
into the field asking for the URL of your github repository then create
the project by selecting OK. As of Fall 2021, Github no longer accepts
usernames and passwords for authentication. However, Rstudio may ask you
for these depending on what version you are using. Don’t be surprised if
you enter your password correctly but your attempt to create a
repository (or push commits to it) still fails because you need to setup
or reset a token.

![If you see this, it means you need to setup or reauthorize a github
token](https://lh3.googleusercontent.com/pw/AM-JKLW24QFJWE5drC-dx2ldqcUZtNvtC-zl6HIiQLUoRYcy9enZV1eomlHk3afwzU_uiythMdAZlKi2eY_nlmdBgpcWcxK5qcZWPnufblrmUYb2bB4YOqBpEQaRqRpQWEX86lRACZFIe2OjFmZYwT30_fYjxA=w704-h296-no?authuser=0)

If you see this message now, go to the **Github 2-factor authentication
(required as of Fall 2021)** section!). If not, you can continue, but
note you’ll have to do it later (when you push changes).

The next screen will bring you to a “normal” RStudio screen.

Before continuing, I recommend turning down the computer usage. Free
rstudiocloud accounts only allow so much usage, but that depends on how
much power you allocate to a project. To do this, click on the RAM icon
in the upper left corner, select resources, and move all sliders to the
far left.

![In Rstudio cloud, move all sliders to the left to give you more actual
hours](https://lh3.googleusercontent.com/pw/AM-JKLVGtN01ndQcB622ioe8eLk0vcbTgdlE2QXG8L_q0scnCBEXjhn4Kvik3Lqm7BoiI11p0YaTYq5NlWaXa303IVly68oNYqfJoQWoNWnAyWUyo5fRcrQ39lrvFBdWP1J-qGd84xGNFN-U1aGgfF5ac6FsAA=w329-h734-no?authuser=0)

If you end up doing something more complex, you can increase allocated
power to speed everything up. For most class code, however, low power
should be fine.) If you make changes here, Rstudio.cloud will need to
relaunch to apply them. Let it do that then keep working.

Continue to the next section (**Now we can actually work in R**) to get
started

## Now we can actually work in R (for everyone!)

Now you can start working on the files in the repository in Rstudio. To
view the files, make sure you are in the right repository. You should
see whatever you named the project in the upper right hand corner of
Rstudio. If you don’t go to File \> Open Project and navigate to where
you placed the repository.

Once you are in the right project, open the file you want to work on.
From inside the project space, go to **File**, **Open File** and find
it, or look in the Files window to find and open the file.

![Use the file tab to navigate to the .rmd
file](https://lh3.googleusercontent.com/pw/ACtC-3esT_YVFqbmcul63AzkXBGrjK5J6kPBMRZW_mT_JNTG7UstxeT9hInq7dA91xV8-e6DbO77u8YepXb6sO6beUo0OlSWg2fXEBbxwgYTHWo7KkZlSAsVfzgpYiL7QbveqRLjctmUYb3RJninK9jMK4DP9A=w800-h452-no?authuser=0)

Then **Knit** the file. Note the first time you do this in a project you
may be prompted to install a number of packages! If you are using a
webservice you may also need to allow pop-ups in your browser.

![The knit button turns your .rmd file into other
products](https://lh3.googleusercontent.com/pw/ACtC-3dlSoGJDHtdGqEBr8L2X-yqZ-08Z95RHUMvaxHqF9EOFcBnqtamYMAWOr75mohUSL_KvWtBTt-u4KrdoHgceHc-sZiViw6l9ZqEQToLIsy6AwvQIQMrJgLbtXfV6gNLDgQvgT3N7aq9pk9-x5ugpegjYA=w378-h109-no)

Then **Knit** the file. Note the first time you do this in a project you
may be prompted to install a number of packages! If you are using a
webservice you may also need to allow pop-ups in your browser. Don’t be
surprised if a new window pops up (it should if you have html output).

The **Knit** button saves the .Rmd file and renders a new version whose
output depends on what you selected in the header. You will see
instructions. As you update the .Rmd file and **Knit** it, it will
update. Make sure you also save changes and **Commit** and **Push** them
back to the github clone! If this is your first time working with a
repository, you can see [instructions for the first assignment for
help](https://github.com/jsgosnell/Starter_code/blob/master/1.%20_Getting_used_to_R/1.-Getting-Used-to-R.md)
for more help.

Note that for your first push (on Desktop) and many pushes (on
Rstudio.cloud) you may need to work with a github token.

![If you see this, it means you need to setup or reauthorize a github
token](https://lh3.googleusercontent.com/pw/AM-JKLW24QFJWE5drC-dx2ldqcUZtNvtC-zl6HIiQLUoRYcy9enZV1eomlHk3afwzU_uiythMdAZlKi2eY_nlmdBgpcWcxK5qcZWPnufblrmUYb2bB4YOqBpEQaRqRpQWEX86lRACZFIe2OjFmZYwT30_fYjxA=w704-h296-no?authuser=0)

### Github 2-factor authentication (required as of Fall 2021)

Github requires you to use a token to verify you have permission to make
changes to repositoties that you store there. To create a token, can use
the code below. If this file is open in R, you can select the green
triangle button (play icon) to run the current chunk. Otherwise you can
copy and paste it into R. Note you may also need to install the usethis
library first.

``` r
library(usethis)
usethis::create_github_token()
```

This will launch a browser pointed to github. You may need to log in.
Then it will have you name a PAT (personal access token). You can, for
example, name it Rstudio. Then scroll to the bottom, and select
**Generate Token**. Save the token somewhere (you’ll never see it again
once you close the window). Then run the next code chunk. Select 3, then
paste in the token you just generated. Again, you may need to install
the gitcreds package.

``` r
library(gitcreds)
gitcreds_set()
```

This process is letting your computer and github communicate and should
only need to be done once for a desktop. For rstudio.cloud, you will
need to regularly reenter the token, but you don’t have to recreate it.
*So save you PAT somewhere just in case*. If/when you lose it, however,
you can simply make a new one and reconnect the repositories.

You’ll continue to update this file eventually turn it in (a little
meta…). For github classroom turning it in just means making sure you
push all changes before the due date.

If this is your first time setting up repositoryyou may run into some
authentication issues. See [instructions for the first assignment for
help](https://github.com/jsgosnell/Starter_code/blob/master/1.%20_Getting_used_to_R/1.-Getting-Used-to-R.md).
