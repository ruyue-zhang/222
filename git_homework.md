1、本地初始化名为learngit的仓库，并配置gitignore文件，忽略掉所有 .class, .log, .jar, .war文件以及.mtj.tmp文件夹下的所有内容。将该本地仓库推送到个人github中。

```
mkdir learngit
cd learngit/
git init
echo ".class .log .jar .war .mtj .tmp" >> .gitignore
git add .
git commit -m "[ruyue] feat:init repository"
git remote add origin https://github.com/ruyue-zhang/learngit.git
git push -u origin master
```

2、仅执行 clone learngit 仓库的 dev 分支到本地。分别使用 switch和checkout命令在本地创建 feature-1 分支并对应到远程该分支。
```
git clone -b dev
git checkout -b feature-1 / git switch -c feature-1
git push origin feature-1
git branch --set-upstream feature-1 origin/feature-1
```

3、当不在同一个地方的两个开发人员需要pair着完成同一个故事卡内容的开发，如何交替使用每个人的电脑进行协同开发？请写出这个过程中所涉及的 git 命令。例如：在 tdd 的过程中，一个人先在自己的机子上写了测试，然后另一个人需要在自己机子上依据测试来写实现。(提示：可以新建一个协同开发分支，分别提交然后拉取的方式，进行协调工作)

+ 首先，A开发测试之后可以用``git push origin <branch-name>``推送自己的修改；
+ B进行代码实现并推送，如果推送失败，则因为远程分支比你的本地更新（A已经push了最新的测试代码），需要先用``git pull``来拉取代码进行合，之后使用``git push origin <branch-name>``进行推送
+ A使用``git pull``拉取代码，如果合并有冲突，则解决冲突，并在本地提交；
+ 没有冲突或者解决掉冲突后，再用``git push origin <branch-name>``推送就能成功！

4、将本地仓库版本回退到两次提交之前的版本后，突然发现回退错了，想将回退后的仓库版本还原到执行回退操作之前的版本。

```
git reset --hard HEAD^^
git reflog //得到回退之前的版本号
git reset --hard [版本号]
```

5、将本地 feature-1 分支内容推到 github 上 git@github.com:cheny/learngit.git 仓库中的 master 分支上。

```
git push origin feature-1 
git branch --set-upstream feature-1 origin/master
```

6、版本发布后，需要给代码库打 tag，tag 名为v0.1，描述信息为version 0.1 released。并将该 tag 推到远程分支。以及如何删除本地和远程仓库名为 v0.9的 tag。

7、开始了一天的工作，先从 feature-1 分支拉取了最新的代码，然后开始对故事卡的内容进行开发。开发到一半的时候，接到 QA 通知，需要在 dev分支上紧急修复一个 bug。当你在dev分支上修复完成并提交后，又有其他人在 dev分支上提交了新的内容。接着收到通知，需要仅仅将修复该 bug 的提交内容合并到 master 分支上，该修复内容之后的提交不能一起合并到 master 分支上。全部操作完成后，回到 feature-1分支继续进行卡的开发工作。（提示： stash 、 cherry-pick）

8、显示提交人为 cheny的从 2020.04.02到 2020.08.06的所有提交记录，只显示提交的 message 即可，不需要显示详细内容。
9、将远程代码库中的提交回滚到 id 为 01e31c的提交。



10、如何修改倒数第 5 次（HEAD~5）提交的 message 信息。如果要将此次修改同步到远程仓库，如何操作？应该注意什么，如果不注意会造成什么后果

11、简述 merge 和 rebase的区别。

12、简述fetch 分别与 pull和 pull --rebase的区别。

13、简述 git 中工作区、暂存区和版本库的区别。

14、简述使用 feature 分支模式进行开发的流程中（拉取代码、创建分支、开发完成后合并分支解决冲突）如何使用一些列的 git 命令。（如 pull, commit, merge, add, fetch,push等）