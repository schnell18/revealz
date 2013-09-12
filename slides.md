<!-- Topic: Version control w/ Git  -->

#Git - A developer perspective

--SLIDE--
Agenda
------
- Version control fundmental
- Git 101
- Setup Git
- Version control in the Git way
  - Git development patterns
  - Common workflows
- Git reference material
- Q & A


--SLIDE--
Version control fundmental
--------------------------
- Tracking history
- Diverge and converge
- Collabration
  - Multiple developers work on same task

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
Gang of four
--------------------
- workspace
- stage (aka index)
- repository
  - local vs remote
  - bare vs development
- stash
![git cmd FSM](/images/git_cmd_state_machine.png)
TODO: insert image to illustrate relationship of the four

--SUBSLIDE--
Git objects
--------------------
- content addressable object
- SHA-1 code
- blob
- tree
- commit
- branch
- tag
TODO: add note to demo the so-called content addressable object
git hash-object -w <file>
git cat-file -p <sha-1>

![Git objects](/images/git_objects.png)

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

[1]: http://code.google.com/p/msysgit/downloads/list?q=full+installer+official+git "Google code Git Windows Binary download page"
[2]: http://www.infoq.com/news/2013/01/vs2012_git "Visual Studio Gets Git"

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
- bash completion and prompt
TODO: add more details on how to setup bash completion and prompt

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
- Unique Git features
  - rebase
  - undo changes


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
--------------------
- Initialize empty repository on central server
  - Use Github like web console
  - Use gitolite
  - git init --bare
- Set up initial repository locally
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
Unique Git features
-------------------
- rebase
- undo changes
  - undo changes in workspace (git checkout -- <file>)
  - undo changes in stage (git reset HEAD -- <file>)
  - undo last commit (git reset --hard HEAD^)
  - fix last commit (git commit --amend)
  - offset previous commit (git revert <sha-1 of previous commit>)


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
