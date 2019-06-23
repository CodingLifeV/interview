**[git学习网址：廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600/896827951938304)**

**一、Git简介**
   * **概述**   
    Git版本控制系统
   * **创建版本库**
初始化一个Git仓库，使用git init命令。
添加文件到Git仓库，分两步：
     1. 使用命令git init命令把这个目录变成Git可以管理的仓库
        >git add <file>
    
        注意，可反复多次使用，添加多个文件；
     2. 使用命令git commit告诉Git，把文件提交到仓库：
        >git commit -m <message>

**二、时光机穿梭**
   * **版本回退**
      1. HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令
         >git reset --hard commit_id。
      
      2. 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本
         >git log
      
      3. 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本
         >git reflog

* **工作区和暂存区：**
 
  工作区（Working Directory）就是你在电脑里能看到的目录；

  工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库，
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

  ![](https://ws1.sinaimg.cn/large/d4556b75ly1g446fllhjcj20ek07v3yo.jpg)

  前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。
   
* **管理修改**
     
    Git跟踪并管理的是修改，而非文件，每次修改，如果不用git add到暂存区，那就不会加入到commit中
* **撤消修改**
   1. 当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令 ：
      >git checkout -- <file>
  2. 当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令 :
     >git reset HEAD <file>
   
      就回到了场景1，第二步按场景1操作。
   3. 已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库
  
* **删除文件**

  一般情况下，你通常直接在文件管理器中把没用的文件删了，或者用rm命令删了：rm gile；这个时候，Git知道你删除了文件，因此，工作区和版本库就不一致了，命令
      
  >git rm <file>

  用于删除一个文件，将版本库中的文件删除，并且需要git commit


**三、远程仓库**

   * **添加远程库**   
   要关联一个远程库，在本地的仓库下使用命令
      >git remote add origin git@server-name:path/repo-name.git
   
      例如：git remote add origin git@github.com:wyjPro/learngit.git
      关联后，如果想取消和该远程仓库的关联，使用：
      >git remote rm origin
      
      通过以下命令把本地仓库的变化强制连接到远程仓库主分支：
      > git pull origin master --allow-unrelated-histories
      
       之后使用命令
      >git push -u origin master

      第一次推送本地版本库master分支的所有内容，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令
此后，每次本地提交后，只要有必要，就可以使用命令
      >git push origin master
   
      推送最新修改
   * **从远程库克隆**
   
      要克隆一个仓库，首先必须知道仓库的地址，然后使用
      >git clone git@server-name:path/repo-name.git
      
     命令克隆。Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

**四、分支管理**
   * **创建与合并分支**
   
      查看分支（git branch命令会列出所有分支，当前分支前面会标一个 * 号）：
      >git branch   
      
      创建分支：
      >git branch <name>

      切换分支：
      >git checkout <name>

     创建+切换分支：
     >git checkout -b <name>

     合并某分支到当前分支：
     >git merge <name>

     删除分支：
     >git branch -d <name>
   * **解决冲突**    
        当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。解决冲突就是把Git合           并失败的文件手动编辑为我们希望的内容，再提交。
        >git log --graph
        
       命令可以看到分支合并图
       冲突如下图：
       ![](https://ws1.sinaimg.cn/large/d4556b75ly1g446pki6vhj20fh08o747.jpg)
       
       现在，master分支和feature1分支各自都分别有新的提交，
       这种情况下，Git无法执行“快速合并”，只能试图把各自的修改合并起来，但这种合并就可能会有冲突，

   * **分支管理策略**
   
     合并分支时，加上
     >--no-ff
   
     参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而
     >fast forward
   
     合并就看不出来曾经做过合并。
   * **Bug分支**  
    修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；当手头工作没有完成时，先把工作现场
        >git stash
        
        一下，然后去修复bug，修复后，再
        
        >git stash pop
        
        回到工作现场
   * **Feature分支**   
    添加一个新功能时，你肯定不希望因为一些实验性质的代码，把主分支搞乱了，所以，每添加一个新功能，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支。   
如果要丢弃一个没有被合并过的分支，可以通过
        >git branch -D <name>

       强行删除
   * **多人协作**  
        查看远程库信息，使用
        >git remote -v

        本地新建的分支如果不推送到远程，对其他人就是不可见的；从本地推送分支，使用
        >git push origin branch-name

        如果推送失败，先用git pull抓取远程的新提交;在本地创建和远程分支对应的分支，使用
        >git checkout -b branch-name origin/branch-name

        本地和远程分支的名称最好一致；建立本地分支和远程分支的关联，使用
        >git branch --set-upstream branch-name origin/branch-name

        从远程抓取分支，使用
        >git pull
        
        如果有冲突，要先处理冲突。
   * **Rebase**

**五、标签管理**

* 使用GitHub
    
  在GitHub上，可以任意**fork**开源仓库；之后自己拥有Fork后的仓库的读写权限；可以推送
        
  >pull request

  给官方仓库来贡献代码。
* **自定义Git**