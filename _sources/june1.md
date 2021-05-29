June 1 ~ Getting Up and Running
============================

## Welcome to Summer 2021

We're all virtual, all remote, and doing what many web development companies have done for years.  This course is here to give you an introduction to the skills and habits used by web developers in their work.  We'll mostly be working together in synchronous Zoom sessions, but there will be time for independent and group work to learn through practice.  We'll start slow, make mini-projects, and gradually build the skills you'll need to complete your projects.

We're all in the same boat during a storm. If you get sick, or need to help others, or need time to get outside tasks done, let's keep in touch and keep lines of communication open.  You can expect empathy and care from the DS staff and your fellow students. Please reach out when you face challenges.     

## Communications and Project Management

- [Slack](https://haverfordds.slack.com) -  If you haven't been added to the course Slack , please write to [me](mailto:ajanco@haverford.edu) or [Mike](mailto:mzarafon@haverford.edu). 
- We'll use Github for all of our project work.  We'll discuss that more in a moment.    
- [DS Cookbook](https://github.com/HCDigitalScholarship/ds-cookbook)
   - Over the years, students in the Libraries' DS program have found good solutions to recurring problems. We don't need to reinvent the wheel or replicate existing code.  The DS cookbook offers short tutorials on common tasks and solutions.


## Code of Conduct and Guiding Principles

- As always, the <a href="https://honorcouncil.haverford.edu/the-code/" target="blank">Honor Code</a> serves as our model. _Trust, concern, and respect_.
- _No one is alone._ We will do our very best to foster a collaborative atmosphere, and welcome your ideas for ways to do so. 
- _Practice self care._ The work environments that we find ourselves in can be isolating, distracting, and exhausting. Self care is not just something you practice during non-work hours, but rather something we do as needed. During the work day, you might find it helpful to do things like:
    - Move around (take a walk or a yoga break)
    - Meditate
    - Grab a healthy snack
    - Share a funny pet photo
- _Embrace failure_. We're going to fail a lot, and it's ok! Failure is how we learn new things. Let's share our failures as well as our successes with each other.
- _Communicate_. Above all else, if you're unsure about what to do next, are having trouble focusing, or are feeling stuck in your work, let someone know!


## Creating a Page with GitHub

In this section, we'll create a very minimal webpage with basic information.
- Who are you?
- What projects are you working on this summer?
- What's your favorite summer food? 

To access GitHub, you will need to create an account. Go to: https://github.com/join  

Once logged in, you can find our GitHub organization here: https://github.com/HCDigitalScholarship


1. [Create a new Github repository](https://docs.github.com/en/github/getting-started-with-github/create-a-repo). Be sure to check the box to "Add a README file." If you forget just follow the instructions in "…create a new repository on the command line." 

2. [Add a new file](https://docs.github.com/en/github/managing-files-in-a-repository/creating-new-files) called `index.html`

3. You can start with the minimum needed then add your own content. 
```html
 <!DOCTYPE html>
<html>
  <body>
    <p>My name:</p> <p>...</p>
    <p>My project(s):</p> <p>...</p>
    <p>Favorite summer food:</p> <p>...</p>
    <a href="https://js-dos.com/games/">a link to something fun</a>
    <!-- add an image if you like -->
    <img src="https://corgiorgy.com/corgiswimflip.gif" />
  </body>
</html>
   ```
4. Add a new blank file called `.nojekyll`
5. [Enable Github pages](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site#creating-your-site) in Settings and note your page's address
6. When done, post your link on Slack. 
7. Feel free to give your page some character and individuality. 


## Python

- For project work this summer, you'll need to have Python installed on your computer.  If that is not possible, you may also work on a virtual machine or cloud notebook.  Ideally, you should work locally if at all possible. 
- If you don't have Python installed, please follow these instructions from [How to Code in Python](https://www.digitalocean.com/community/books/digitalocean-ebook-how-to-code-in-python) by Lisa Tagliaferri.
- You'll also need to install pip, which is a tool for installing packaged Python libraries.  If you're using Conda (covered next) you don't need to do this.  Otherwise, follow [these instructions](https://pip.pypa.io/en/stable/installing/). 
- Once you have Python and pip installed on your machine, you can create virtual environments, which are a tool to manage dependencies.

To install virtualenv:
`pip install virtualenv`

To create a virtualenv:
`virtualenv my_env_name`
you will see a new directory called my_env_name in your current directory.

To enter the virtualenv:
`source ./my_env_name/bin/activate`
you should see a (my_env_name) in the command line.  This indicates your current working environment.  

To exit the environment `deactivate`

# Common Commands

Now that you have Python and virtualenv or conda installed, we can start to explore the command line.  It is one of the most central tools you'll use to navigate between directories, copy and move files, edit code, configure servers, and other tasks. 

---

![Ted Underwood's debugging rules https://twitter.com/Ted_Underwood/status/1388842971395764231](_static/debugging.png)

---

## Moving or renaming files
- `cp`
   - `<cp> <origin> <destination>`
   - ex: `cp file.txt ./site/static`

- `mv` (also to change names)
   - ex: `mv file.txt ./site/static`

---

- `-r` is needed when copying a directory
- `-f` is used to force a yes answer to all questions.  Otherwise you may need to confirm move or copy of every file in a directory
   -ex: `cp -rf ./mydir ./home/`

-  `rm`
   - ex: `rm -rf ./mydir`

---

## Editing code
- `vim` [basic commands](https://coderwall.com/p/adv71w/basic-vim-commands-for-getting-started)

- `nano` [basic commands](https://wiki.gentoo.org/wiki/Nano/Basics_Guide)

---

## Connecting to servers
- `ssh ajanco@bridge.haverford.edu`
- from server to local: `scp ajanco@bridge.haverford.edu:/home/ajanco/myfile.txt .`
- from local to server: `scp myfile.txt ajanco@bridge.haverford.edu:/tmp`

---

## Services
- `service nginx restart`
- `service uwsgi restart`

---

## psql 

- `sudo -u postgres createdb <db_name>`
- `sudo -u postgres removedb <db_name>`
[more](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)


## Code Editors 

---

## VSCode
<img src="https://user-images.githubusercontent.com/674621/71187801-14e60a80-2280-11ea-94c9-e56576f76baf.png" alt="This image is in /static" width="25%">

Visual Studio Code is currently one of the most popular code editors.  It's simple and handle most of what you'll need this semester. 

[Download here](https://code.visualstudio.com/)


---

<iframe width="100%" height="400px" src="https://www.youtube.com/embed/W--_EOzdTHk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

## PyCharm 

PyCharm is a full-featured Integrated Development Environment (IDE).  It basically does everything. As a student, you can sign up for a [free educational license here](https://www.jetbrains.com/community/education/#students).
Like Photoshop, PyCharm can feel a bit daunting at times and takes time to learn.  It does everything, but you need to learn how it does everything.  Many professional developers swear by it.  Andy's classes in graduate school used it, so it's something worth knowing, even if it's not your go-to code editor for every project. 

Real Python has a [great guide on PyCharm](https://realpython.com/pycharm-guide/) for further info.

---

<img src="https://lever-client-logos.s3.amazonaws.com/b2b59285-235a-438e-8acd-a00e9ff37245-1537838422416.png" width="25%" />

Whatever code editor you're using, we recommend also installing [Kite](https://www.kite.com/).

Kite is kind a great tool for seeing how other people write their code. As you write, the co-pilot will display the documentation for whatever you're using and share examples of how other people use that library.  It's a great way to keep track of current best practices and the range of opinions on how best to use particular tools. 

---

<video width="100%" controls autoplay name="media">
<source src="https://www.kite.com/wp-content/uploads/2020/05/JavaScript-video-main-light-mode-65-resolution.mp4" type="video/mp4">
</video>

---

<img src="https://warehouse-camo.ingress.cmh1.psfhosted.org/0fec70e46ca299f4ec9d49a417c04795107b74f0/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f7073662f626c61636b2f6d61737465722f646f63732f5f7374617469632f6c6f676f322d726561646d652e706e67" width="25%" />

Developers are very picky about the look and style of their code.  One of the best ways to make your code less smelly is to use a code formatter.  [Black](https://pypi.org/project/black/) is very good for this.  

The main problem with Black is that is does all the work for you.  If you're interested in learning and better understanding the [Python PEP8 Style Guide](https://www.python.org/dev/peps/pep-0008/), PyCharm has style auto-suggest.  You can also [use pylint in VSCode](https://code.visualstudio.com/docs/python/linting).



## [Conda](https://www.anaconda.com/products/individual)

When working locally, I prefer anaconda. Conda is also very helpful if you're using a Windows machine.  It will give you a similar environment to those working on Unix and Linux machines.

Conda is very similar to virtualenv, but is able to handle far more complicated dependencies.  For example, if you are using a GPU for computation with the CUDA library it can be daunting to install all the dependencies by hand.  However, a simple `conda install tensorflow-gpu` or `conda install pytorch-gpu` will install everything you need.  It is also useful with C-compiled libraries such as OpenCV (`conda install opencv`).  

[cheat sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)


## Git and version control

We use git for everything.  You may already know and use it.  Whatever you already know, we'd like to spend a few minutes talking about how we use Git and what we expect you to know.  


---

Always first:
```git pull ```

If you're in a project directory that is tracked by git, `git pull` will check with GitHub for any new changes and update your local copy.  Imagine spending an hour writing code, it's brilliant, only to get a "merge conflict."  Someone else already wrote that.  

---

You can also:
```git status```

This will show any differences between your copy of the project and the repository. If you've added new files that need to be tracked, they'll appear in red.  As a habit, it's good to `git status` before you start a commit.  This will help you establish what's new and what will be added to the commit.

---

```git checkout```
This command is used to switch branches. The default branch is `master`. For many projects, you'll be asked to work on your own branch or to create a branch for each issue. You can change branches with `git checkout branch_name`. If you want to create a branch and move into it enter `git checkout -b ajanco`.    

---

```git add```
When you create a repository you use `git init`.  This tell git to track changes in a directory and its subdirectories. As you add new files to the folders, you need to tell git to track them.  You can use `git add .` to track all files, but this is sloppy.  Many many times you'll have throw away files or files with sensitive information that you don't want to push to GitHub. Just `git add my_file.txt` and it will start tracking a new file. 

---

```git commit -am "commit message"```
Now you just need to commit your changes.  The `-a` tag will include changes to all tracked files and `-m` appends a message.  Commit messages are not for you.  They're a message to other coders that explains what was accomplished in the commit. It's very tempting to flake on this and write "changed stuff" or "fixed bug."  In the commit we can see the changes that were made.  What we don't know is why the changes were made.  Give some context, name the issue or problem that you addressed: "Fixed Issue #23: images now sized correctly on mobile."  

[bonus: The Most Frequent Commit Messages on GitHub are Mostly Useless](https://ramiro.org/blog/most-frequent-github-commit-messages/)

---

```git push```

Now that your changes are staged, you can push them to the repository. They're now safe and living in the cloud.  Keep in mind that most of our projects are public and other people can see your code.  Never never ever ever please do not push settings_secret.py files or files with API keys, or other sensitive information.  Add all such files to `.gitignore`. They won't be tracked, and better yet, they'll never end up on the web.  People crawl GitHub for passwords and any sneaky ways to turn you project into a crypto-mining, spam sending, toxic malware festival.  Cleaning up a worm-infested meltdown is no fun.      

---

```git merge```
Let's say I added a new feature in the `ajanco` branch and they're ready to add to the project's code base. I'd switch back to master with `git checkout master` and then pull my changes from other branch with `git merge ajanco`. Alternatively, I can go to the project's GitHub page, click "Pull requests" and "New Pull Request."

In many projects, someone will be notified and inspect your new code.  You'll get comments back and it's a nice way to chit-chat about our work.  Once approved the code enters the master branch and will be deployed shortly.   

---

## further reading

[try.github.io](https://try.github.io/)

[Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

[The seven rules of a great Git commit message](https://chris.beams.io/posts/git-commit/)


## Web Development Community

- Industry is constantly changing as new frameworks are developed, standards change and fashion demands novelty.  To keep apace with the field, it's important to follow the discussion.  

Here are a few places that I follow for news:  
- [Medium](https://medium.com/)
- [Papers with Code](https://paperswithcode.com/)
- Twitter (here are some good people to follow)

Sebastián Ramírez  dev of FastAPI, Typer
@tiangolo
https://github.com/tiangolo

Erika Heidi, Digital Ocean Senior Technical Writer
@erikaheidi
http://www.erikaheidi.com/

Peter Baumgartner, Research Data Scientist
@pmbaumgartner
https://pmbaumgartner.github.io/

Sarah Drasner, CSS, Netlify
@sarah_edo
https://sarahdrasnerdesign.com/

Cassidy Williams
@cassidoo
https://cassidoo.co/

Mariatta, Python Core Developer
@mariatta
https://mariatta.ca/

Nina Zakharenko, Python
@nnja
https://www.nnja.io/

Ken Reitz, Requests, Python
@ken_reitz
https://kenreitz.org/

Lisa Tagliaferri, MIT, Digital Ocean, Python
@lisaironcutter
https://lisatagliaferri.com/

Simon Willison, co-creator of Django
@simonw
https://simonwillison.net/

Russell Keith-Magee, Django Core Developer
@freakboy3742

Matthew Honnibal, spaCy, Thinc, NLP
@honnibal
https://explosion.ai/about

Ines Montani, spaCy, Prodigy, Gatsby, UI
@_inesmontani
https://ines.io/

David Ha, research scientist at google brain in Tokyo
@hardmaru
https://otoro.net


