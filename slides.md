<!--
title: Git - A developer perspective
author: Justin Zhang
-->

##Git - A developer perspective

<aside class="notes">
State purpose of this kicks: share some personal Git experience, promote Git usage for both work and private. Kick off w/ Yesmobile story on VCS softwares eval: ClearCase, Visual Source Safe, CVS, Senior SE bias of CVS, Department manager preference on PVCS, zip keeping blunder.
</aside> 

--SLIDE--
Agenda
------
- What is version control
- Git 101
- Git workflows
- Git in action
- How to dig into Git
- Q & A

<aside class="notes">
State the overall content of this presentation: concept, demo and quiz
/aside> 


--SLIDE--
What is version control
-----------------------
- Control the right content
- Track changes
- Diverge and converge
- Collabration

<aside class="notes">
**Source** code is the key component to control, do not keep derivates.
Take example of maintenance of old version, auditing to illustrate track changes.
Take example of release and dev activity to illustrate diverge and converge.
Take example of global team to illustrate collabration challenge such as timezone
and how git resolve it.
</aside> 


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
------------
- workspace
- stage (aka index)
- repository
  - local vs remote
  - bare vs development
- stash

--SUBSLIDE--
File status in Git
------------------
- new
- modified
- staged
- committed
- ignored
- untracked

<aside class="notes">
demo the file status
</aside>

--SUBSLIDE--
![git cmd FSM](/images/git_cmd_state_machine.png)

<aside class="notes">
illustrate workspace/index/repository/stash and common git operations by following the diagram
index: stage or cache, a set of changeset prepared for commit; not in SVN
</aside>

--SUBSLIDE--
> If you deny the index, you really deny git itself.
> --Linus Torvalds February 4, 2006, Git List Archives
<aside class="notes">
stress the importance of understanding index, a lot of git command depends on index
</aside>

--SUBSLIDE--
Quick quiz
----------
<p class="gitkicks">Wally appends statment</p>

    printf("Job well done!\n");

<p class="gitkicks">to the end of program main.c and stage it into index, then he think it is worth mentioning the promotion, so he add another line:</p>

    printf("Consider double the salary!\n");

<p class="gitkicks"> to end. If Wally commits right now, what will be the last line in the repository?</p>

-----------
- A. printf("Job well done!\n");
- B. printf("Consider double the salary!\n");
- C. the same as before

<aside class="notes">
 Make a quick demo, depending on the response of audience.
</aside>

--SUBSLIDE--
Git objects
--------------------
- content addressable object
- SHA-1 code
- Git object types
  - blob
  - tree
  - commit
  - branch
  - tag

<aside class="notes">
demo content addressable object and sha-1
git hash-object -w <file>
git cat-file -p <sha-1>
</aside>

--SUBSLIDE--
![Git objects](/images/git_objects.png)

--SUBSLIDE--
Unique Git features
-------------------
- rebase
- porcelain and plumbing commands
- modify commit history
  - undo changes in workspace (git checkout -- <file>)
  - undo changes in stage (git reset HEAD -- <file>)
  - undo last commit (git reset --hard HEAD^)
  - fix last commit (git commit --amend)
  - offset previous commit (git revert <sha-1 of previous commit>)

<aside class="notes">
Draw commit history tree on white board to illustrate rebase
</aside>


--SLIDE--
Version control in the Git way
------------------------------
- Git development patterns
- Enterprise development using Git
  - Branching scheme
- Common workflows

--SLIDE--
Common Git development patterns
-------------------------------
- Central repository pattern
- Integration manger pattern
- Dictator-lieutenants pattern

--SUBSLIDE--
![Central repository pattern](/images/central_pattern.png)

--SUBSLIDE--
![Integration manager pattern](/images/integration_manager_pattern.png)

--SUBSLIDE--
![Dictator-lieutenants pattern](/images/dictator_lieutenants_pattern.png)


--SLIDE--
Enterprise development using Git
--------------------------------
- Branching scheme
- Centralized similar to Subversion
- Typical workflows
  - Setup Git repository
  - Develop new feature
  - Make patch/hotfix

--SUBSLIDE--
![RnD branching scheme](/images/rnd_branching_scheme.png)


--SLIDE--
Common workflows
----------------
- Setup Git repository
- Develop new feature
- Make patch/hotfix
- Integrate pull request

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

--SUBSLIDE--
Make patch/hotfix
-----------------
- create patch/hotfix branch
- make and stage local changes
  - add new file (git add <new_file>)
  - modify existing file (git add <file>)
  - delete file (git rm <file>)
- test
- commit changes (git commit -m "your comment message")
- git push origin <patch_branch>


--SLIDE--
Git in action
-------------
- setup git
  - install git
  - configure git
- manage your project with Git


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

<aside class="notes">
Recommend use command line git for beginner so that he can understand Git better.
</aside>

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

[1]: https://help.github.com/articles/dealing-with-line-endings "dealing with line endings"

--SUBSLIDE--
Sample Git configure
--------------------
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

--SUBSLIDE--
bash completion & prompt
------------------------
- bash completion
  - tab to complete the git command
  - get [bash completion][1] from github
  - copy git-completion.bash into /etc/bash_completion.d
  - MacOS X user: install homebrew
- bash prompt
  - show branch and merge status on command line prompt
  - get [bash prompt][2] from github
  - copy git-prompt.sh as .git-prompt.sh into your home directory
  - add following lines into your .bash_profile


        if [ -f ~/.git-prompt.sh ]; then
            source ~/.git-prompt.sh
            export PS1='[\u@\h \W$(__git_ps1 " (%s)")]\$ '
        fi  
 
[1]: https://github.com/git/git/blob/master/contrib/completion/git-completion.bash "bash completion"
[2]: https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh

<aside class="notes">
Demo the git completion and git prompt
</aside>


--SUBSLIDE--
Develop with Git example
------------------------
- Determine git server option
  - git hosting service ([GitHub][1], [Bitbucket][2])
  - internal git server (gitolite)
- Develop, maintain project
  - setup project
  - program-test-commit-publish loop
  - accept patches

[1]: http://github.com "GitHub"
[2]: http://bitbucket.com "Atlassian Bitbucket"

--SLIDE--
Demo time ...
-------------
<aside class="notes">
Demo git_kicks project: init, add initial source, commit, push to remote, modify
Demo files status, stage process as quiz
</aside>


--SLIDE--
So how do I study Git effectively?
----------------------------------

--SUBSLIDE--
books
-----
- *Pro Git* [1]
- *Version Control with Git 2nd* [2]

[1]: http://git-scm.com/book "Pro Git"
[2]: http://shop.oreilly.com/product/0636920022862.do?green=62C71D50-BC4E-5575-BDAB-B7F3ECD001BC&intcmp=af-mybuy-0636920022862.IP "Version Control with Git 2nd"

--SUBSLIDE--
Online video
------------
- *Git for Ages 4 and Up* [1]
- *Vimcast fugitive series* [2]

[1]: http://www.youtube.com/watch?v=1ffBJ4sVUb4 "Git for Ages 4 and Up - Youtoube"
[2]: http://vimcasts.org/episodes/fugitive-vim---a-complement-to-command-line-git/ "Fugitive.vim - a complement to command line git"
--SUBSLIDE--
> And start your own project on GitHub[1] **NOW**

[1]: http://github.org "GitHub"

--SUBSLIDE--
One more thing ...

--SUBSLIDE--
![RTFM](/images/rtfm.png)


--SLIDE--
![Octocat Network](/images/ask_octocat.png)
