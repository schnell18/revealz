<!-- Topic: Version control w/ Git  -->

<h1>Git</h1>

--SLIDE--
Agenda
-------
- Version control stories
- Git 101
- Setup Git
  - Install Git
  - Configure Git
- Version control in the Git way
  - Git development patterns
  - Common workflows
- Git learning material
- Q & A

--SLIDE--
Git 101
---------
- Developed by Linus to manage Linux kernel
- Distributed Version Control System(DVCS)
  - no central repository required
  - support disconnected development
- Advantages
  - Super fast
  - Efficient disk space usage
  - Powerful branch and merge

--SUBSLIDE--
Git objects model
--------------------
- workspace, stage, repository and stash
- object store
  - SHA-1 code
  - blob
  - tree
  - commit

--SUBSLIDE--
Git objects
--------------------
- SHA-1 code
- blob
- tree
- commit

![Git objects](/images/git_objects.png)

--SUBSLIDE--
Git concepts
-------------
- refs
- repository
  - content addressable object
  - local repository
  - remote repository
  - bare repository
  - development repository
- submodule
- branch
- tag

--SUBSLIDE--
Git concepts(cont)
-------------
- clone
- init
- stage
- commit
- checkout
- branch
- merge
  - fast-forward merge
  - three-way merge
  - recursive merge
  - octpus merge
  - ours merge
  - subtree merge
- rebase
- push
- fetch
- pull

 
--SLIDE--
Setup Git
---------
- Install offical Git
  - install from source
  - install from binary (.deb, .rpm, ports, msysgit[1])
- Third party Git clients
  - Github
  - TortoiseGit
  - IDEs (Eclipse, Xcode, Visual Studio[2])
- Configure Git

[1]: http://www.infoq.com/news/2013/01/vs2012_git "Visual Studio Gets Git"
[2]: http://code.google.com/p/msysgit/downloads/list?q=full+installer+official+git "Google code Git Windows Binary download page"

--SUBSLIDE--
Configure Git
-------------
- git config
- Scope
  - system (/etc/gitconfig)
  - global ($HOME/.gitconfig)
  - project ($GITDIR/config)
- Important items
  - user name (user.name)
  - email (user.email)
  - line ending (see [dealing with line endings][1])
    -input for Unix/MacOS X/Linux, auto for Windows
  - command aliases

[1]: https://help.github.com/articles/dealing-with-line-endings "dealing with line endings"

--SUBSLIDE--
Sample Git configure
-------------
    git config --global user.name "Justin Zhang"
    git config --global user.email "fgz@qad.com"
    git config --global core.editor vim
    git config --global core.autocrlf true
    git config --global color.ui true
    git config --global merge.tool vimdiff
    git config --global push.default simple
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.ci commit
    git config --global alias.st status
    git config --global alias.dfs "diff --staged"
    git config --global alias.logg "log --graph --decorate --oneline --abbrev-commit --all"
    git config --global alias.unstage 'reset HEAD --'
    git config --global alias.last 'log -1 HEAD'

--SLIDE--
Version control in the Git way
------------------------------
- Git development patterns
  - Central repository pattern
  - Integration manger pattern
  - Dictator-lieutenants pattern
- Enterprise development using Git
  - Branching scheme
  - Common workflows

--SLIDE--
Enterprise development using Git
--------------------------------
- Branching schem
- Centralized similar to Subversion
- Typical workflows
  - Setup Git repository
  - Develop new feature
  - Make patch/hotfix

--SUBSLIDE--
Branching scheme
----------------
TODO: insert picture here

--SUBSLIDE--
Setup Git repository
------------------------------------------------
- Initialize empty repository on central server
- Set up initial repoistory locally
  - mkdir proj1 && cd proj1
  - git init
  - add project content, ignore, attribute file etc
  - git add .
  - git commit
- push local repository to central
  - git remote add origin <url_to_central_git_repo>
  - git push origin --all

--SUBSLIDE--
Develop new feature
-------------------
- git clone or git pull
- optionally create and switch to feature branch
- make and stage local changes
  - add new file (git add <new_file>)
  - modify existing file (git add <file>)
  - delete file (git rm <file>)
- test
- commit changes (git commit -m "your comment message")
- merge feature to project branch
- git push origin <proj_branch>


--SLIDE--
Git reference material
----------------------
- books:
  - *Pro Git* [1]
  - *Version Control with Git 2nd* [2]
- Online video:
  - *Git for Ages 4 and Up* [3]
  - *Vimcast fugitive series* [4]

[1]: http://git-scm.com/book "Pro Git"
[2]: http://shop.oreilly.com/product/0636920022862.do?green=62C71D50-BC4E-5575-BDAB-B7F3ECD001BC&intcmp=af-mybuy-0636920022862.IP "Version Control with Git 2nd"
[3]: http://www.youtube.com/watch?v=1ffBJ4sVUb4 "Git for Ages 4 and Up - Youtoube"
[4]: http://vimcasts.org/episodes/fugitive-vim---a-complement-to-command-line-git/ "Fugitive.vim - a complement to command line git"

--SLIDE--
![Octocat Network](/images/ask_octocat.png)
