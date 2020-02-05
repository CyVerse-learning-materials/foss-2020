.. include:: ../cyverse_rst_defined_substitutions.txt

|CyVerse_logo2|_

|Home_Icon2|_
`Learning Center Home <http://learning.cyverse.org/>`_

**Version Control**
===================

`Version Control <https://en.wikipedia.org/wiki/Version_control>`_ is an important component in software development which manages changes to documents, websites, code, or other digital information. Version control can save you when code changes break things. Web hosting of your code repositories lets you share and work on code together and save your work in the event of a hardware failure. 

The `most commmon version control software <https://en.wikipedia.org/wiki/List_of_version-control_software>`_ in data science are ``git``, ``svn``, ``cvs``, and ``bzr``.

Given the limited amount of time we have this week, we are only going to cover `Git <https://git-scm.com/>`_ and one web-based hosting service (`GitHub <https://github.com/>`_) in this camp.


**GitHub**
==========

**Setup**
---------

1. Create an account on GitHub:

   - `GitHub <https://github.com/>`_

2. Create an *organization* on GitHub.

   - `GitHub Organization <https://help.github.com/en/enterprise/2.19/admin/user-management/creating-organizations>`_

 3. Create a folder on your computer titled "GitHub"

 4. Create a subfolder on your computer titled "Lab"

 5. Install Git
 	- `Download <https://git-scm.com/downloads>`_

**Introduction**
----------------

We will learn how to:

- Interact with the GitHub environment
	- Using the web interface
	- Using command line

- Create a repository
- Best practices
- Create an issue
- Push/pull files
- Commit to GitHub
- Add collaborators
- Branching
- Pull requests
- Merging

- Advanced GitHub
	- Fork
	- Releases

Goals:
- Learn the importance of Version Control
- Feel comfortable using the GitHub environment
- Integrate at least one research project on GitHub

**Background**
--------------

GitHub Uses
~~~~~~~~~~~

- Version control
- Collaborative projects
- Creating websites
- Teaching tools
- Software development
- Code development

**NOTE** Not really for storing or manipulating data

**Navigating & Interacting with GitHub**
------------------------------------------

Basic Layout
~~~~~~~~~~~~

|GitHub|

The basic layout includes:
- Profile
- Organizations
	- These are larger groups that may have multiple repositories
- Teams
	- These are groups within Organizations
- Repositories
- `Projects <https://help.github.com/en/articles/about-project-boards>`_
- Followers
- Contributions
- Watch / Unwatch repos

**Add a Collaborator**
~~~~~~~~~~~~~~~~~~~~~~

*Online only*

1. Go to your Organization
2. Click "people"
3. Invite someone!

OR

1. Can add collaborators under "Settings" -> "Collaborators"

**Create a Repo Online & Locally**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Online*

1. Go to your dasboard
2. Click "New"
3. Name the repository
4. Initialize with "README"
	- form of metadata
	- this tells you and the those looking at the repository what it is about
5. Go to "Clone or Download" and clone to local folder / directory titled "Lab"

Can delete repo under "Settings" -> "Options"


*Command Line*

1. Locate local folder / directory titled "Lab"
.. code-block:: 
	cd path/to/location
	mkdir <folder_name>
	cd <folder_name>

2. Add to GitHub
.. code-block:: 
	git init
	git add *.c
	git add .gitignore
	git commit -m "initial project"

**NOTE** Documentation is vital. *You are doing this for you 6 months from now*

**Interact with GitHub**
~~~~~~~~~~~~~~~~~~~~~~~~

**Clone a repo**
This is used to work *locally* rather than online.

*Online*

1. Click the down arrow "Clone or download"
2. Click "Open in Desktop"
3. Select where to save it
	- Create a folder for GitHub repos on your computer locally

*Command Line*

.. code-block:: 
	cd path/to/location
	git clone <url> rename
	#URL of thte repository on GitHub
	#rename the directory (optional)

**Commit**

*Online*

1. Create a file  by clicking "Create a new file"
2. Name file (/name)
3. Write commit message
4. Press "Commit"

OR

1. Create a file *locally*
2. Click "Upload files"
3. Select file(s) within a folder
	To create a folder click on "New File", then type FileName/
	Add .gitkeep (convention to create an *empty* folder)

*Command Line*

1. Create a file
.. code-block:: 
	cd path/to/repo
	touch file.txt

2. Add file(s)
.. code-block:: 
	git add -A #adds all the new files
	git push
	git commit -m "added file" #-m initiates a message

**tip** It is good practice to write commmit messages to remember what you added or fixed.

**Create an Issue**

Issues are great for tracking decisions made or to-do lists

*Online only*

1. Click on the repository you just created.
2. Click on "Issues"
3. Click on "New issue"
4. Create a title
	- this will have a hastag (#) and issue number that you can refer to later in the comments
5. Assign to someone, or create a label
6. Submit new issue
7. Close issue

**Exercise:**
1. Create a new issue and relate it back to the issue you just created.


**Version Control**
*You are doing this for you 6 months from now*

*Online*

1. Click on file
2. Click "History"

*Command Line*

.. code-block:: 
	git log
	git log --stat #gives abbreviated stats for each commit
	git log --pretty=oneline #can also add options: short, full, fuller
	git log --pretty=format:"%h - %an, %ar : %s #lots of options for pretty=format
	
	:q #to quit

**Create a branch**
Branches are useful to working on code etc. without disturbing the *master branch*.

*Online*

1. Select the down arrow on the repository page that says "Branch:master"
2. Create a new branch name

OR

1. Add new file or edit existing file.
2. Write a commit message.
3. Select "Create a **new branch**"

*Command Line*

.. code-block:: 
	cd path/to/repo
	git fetch
	git pull
	git checkout -b new-branch #see which branch you are on
	git branch new-branch #create a new branch

.. code-block:: 
	<edit files>
	vi path/to/file
	:q #to quit

OR
.. code-block:: 
	nano path/to/file

.. code-block:: 	
	git push origin new-branch

	git branch -a #see all branches 

	git branch -d new-branch #delete branch locally
	git branch origin :'new-branch #delte branch on GitHub

**Make a pull request**
Pull requests are useful to have another set of eyes to review changes  before merging them with the master branch.

*Online*

1. From your branch, create a new file
2. Commit file to your branch
3. Hit "Compare & pull request"
4. Go to pull requests
5. "Merge pull request"
6. Delete branch
7. Set it on the master branch

*Command Line*

.. code-block:: 
	cd path/to/repo
	git pull
	git status
	git checkout -b new-branch
	<edit files>
	git add -A #"A" add all the files
	git push --set-upstream origin new-branch
	git commit - m "did some things"

**Merge**

*Online*

1. Go to "Pull requests"
2. Select down arrow of "Merge pull request"
3. Merge, Squash, or Rebase OR ignore
4. Leave comment if need be
5. Close pull request

*Command Line*

.. code-block:: 
	cd path/to/repo
	git pull
	git checkout master
	git merge new-branch
	git branch -d new-branch

**Advanced**
~~~~~~~~~~~~

**Fork**

*Online*

1. Go to a new repository
2. Click fork
3. Save to personal repository.
4. Clone to Desktop.
5. Interact via online or in Desktop.
6. If want to make suggestions, can create a pull request.

*Command Line*

.. code-block:: 
	git close <github-repo>
	cd <new-folder>
	git fork

**Etc.**
~~~~~~~~
These are *Online only*

- Versioning 
	1. Go to "Releases"
	2. Click "Create a new release"
	3. Tag version: Version #
	4. Release title: I usually put the date of the release, but any system can work

- Reactions:
	1. Create a new pull request
	2. Looking at the messages, click the smiley face to give a reaction

- Badges
	1. Go find a `badge <https://naereen.github.io/badges/>`_!
	2. Copy badge code into README:



**Definitions**
~~~~~~~~~~~~~~~

*Git* - tool for version control.

*GitHub* - hosted server that is also interactive.

*repo* - short for repository; GitHub lets you create a remote repository online.

*local* - on your personal computer.

*clone* - copy of a repository that lives locally on your computer. Pushing changes will affect the repository online.

*fetch* - getting latest changes to the repository on your local computer.

*branch* - parallel to the master branch; allows you to make changes without affecting the master branch. Changes made on a branch can be merged back to the master.

*fork* - copy of someone else's repository stored locally on your account. From forks, you can make pull requests to the master branch.

*upstream* - primary or master branch of original repository.

*downstream* - branch or fork of repository.

*untracked* - changes made locally but not yet commited or pushed to the online repo.

*staged* - item added to the repo.

*commit* - finalize a change.

*push* - add changes back to the remote repository.

*merge* - takes changes from a branch or fork and applies them to the master.

*pull request* - proposed changes to/within a repository.

*issue* - suggestions or tasks needed for the repository. Allows you to track decisions, bugs with the repository, etc.


**Git cheat sheet**
~~~~~~~~~~~~~~~~~~~

Here is a list of the most important commands in Git:

.. list-table::
    :header-rows: 1

    * - Git Task
      - Command
      - Description 
    * - Set up your profile locally
      - ``git config --global user.name "Cy Unicorn"``
      - Set your user name
    * - 
      - ``git config --global user.email Cy1@cyverse.org``
      - Set your email address
    * - Create a Repository locally
      - ``git init``
      - Initialize a folder as a  ``git`` repository
    * - Get an existing repository from a web service
      - ``git clone ssh://git@github.com/[username]/[repository-name].git`` 
      - Create a local copy of a remote repository

.. list-table::
    :header-rows: 1

    * - Basic Snapshots
      - Command
      - Description 
    * - 
      - ``git status`` 
      - Check status of the repository
    * -  
      - ``git add [file-name.txt]`` 
      - Add a file to "the staging area"
    * -
      - ``git add -A`` 
      - Add all new and changed files to "the staging area" 
    * -
      - ``git commit -m "[brief commit message]"``
      - Commit changes to "the staging area"
    * - 
      - ``git rm -r [file-name.txt]`` 
      - Remove a file (or folder) 
    * -
      -`git push` 
      - Push changes to remote repository (remembered branch)

.. list-table::
    :header-rows: 1

    * - Branching & Merging
      - Command
      - Description 
    * -
      - ``git branch`` 
      - List branches (the asterisk denotes the current branch) 
    * -
      - ``git branch -a`` 
      - List all branches (local and remote) 
    * -
      - ``git branch [branch name]`` 
      - Create a new branch 
    * -
      - ``git branch -d [branch name]`` 
      - Delete a branch 
    * - 
      - ``git push origin --delete [branch name]``
      - Delete a remote branch 
    * - 
      - ``git checkout -b [branch name]`` 
      - Create a new branch and switch to it 
    * - 
      - ``git checkout -b [branch name] origin/[branch name]`` 
      - Clone a remote branch and switch to it 
    * - 
      - ``git checkout [branch name]`` 
      - Switch to a branch 
    * - 
      - ``git checkout -`` 
      - Switch to the branch last checked out 
    * -  
      - ``git checkout -- [file-name.txt]`` 
      - Discard changes to a file 
    * - 
      - ``git merge [branch name]`` 
      - Merge a branch into the active branch 
    * - 
      - ``git merge [source branch] [target branch]`` 
      - Merge a branch into a target branch 
    * - 
      - ``git stash`` 
      - Stash changes in a dirty working directory 
    * - 
      - ``git stash clear`` 
      - Remove all stashed entries 

.. list-table::
    :header-rows: 1

    * - Sharing & Updating Projects
      - Command
      - Description 
    * -       
      - ``git push origin [branch name]`` 
      - Push a branch to your remote repository 
    * -       
      - ``git push -u origin [branch name]`` 
      - Push changes to remote repository (and remember the branch)
    * - 
      - ``git push`` 
      - Push changes to remote repository (remembered branch)
    * - 
      - ``git push origin --delete [branch name]`` 
      - Delete a remote branch
    * - 
      - ``git pull`` 
      - Update local repository to the newest commit
    * - 
      - ``git pull origin [branch name]`` 
      - Pull changes from remote repository 
    * - 
      - ``git remote add origin ssh://git@github.com/[username]/[repository-name].git`` 
      - Add a remote repository 
    * - 
      - ``git remote set-url origin ssh://git@github.com/[username]/[repository-name].git`` 
      - Set a repository's origin branch to SSH 

.. list-table::
    :header-rows: 1

    * - Inspection & Comparison
      - Command
      - Description 
    * - 
      - ``git log`` 
      - View changes
    * - 
      - ``git log --summary`` 
      - View changes (detailed)
    * - 
      - ``git diff [source branch] [target branch]`` 
      - Preview changes before merging
