# Git命令参考手册(文本版) [https://www.oschina.net/question/156344_148084]


# git学习视频，以下笔记来自视频米斯特吴上课，讲课的话。我给记录下来了。


# 视频地址：[https://ke.qq.com/course/237926]


# git学习笔记

什么是git
版本管理控制工具（vcs）

1. 分布式版本控制

2. 多个开发人员协调工作

3. 有效监听谁做的修改

4. 本地及远程操作


// 在公司里面往往是做项目，一个项目是一个人完成
// 也可能是多个人完成。

// 完成项目的时候，需要对你完成的代码进行控制，
// 这个就需要用到git

// git可以帮助我们做什么工作
// 第一：分布式的版本控制，因为整个项目会分给多个人去开发
// 每个人都可以通过git，知道自己所做的项目，所写的代码
// 然后呢就可以进行分布式的管理

// 第二：多个开发人员协调工作，如果我们有多个开发人员，想去看看，别人写的代码的话
// 可以通过git，把你想知道的对应的代码拉取下来
// 你写完的代码也可以把把它上传上去
// 这样子的话就可以，协同办公

// 第三：有效监听谁做的修改，最主要的是我们可以责任到己，
// 每一个开发人员，他们在任务的时候，写代码的时候，难免会有一些修改，
// 甚至是说，在我们上传我们写的文件的过程，难免会有些错误
// 我们可以通过git去知道，谁把代码写错了。
// 在具体的历史记录中就可以看得到

// 最后：是本地及远程的操作，我们可以通过git的去操作本地的仓库，同样我们也可以
// 把本地的代码上传到，git远程仓库里面去。


#### git的基础命令行操作
```s
$  git init       初始化本地git仓库
$  git add<file>  添加文件
$  git status     查看状态
$  git commit     提交，提交到本地的git仓库里
$  git push       推送到仓库，推送到远程仓库
$  git pull       从远程仓库拉取数据
$  git clone      从远程仓库拷贝数据
```
#### 安装git，到官网去安装  略

01. 打开终端，git --version，提示版本号，即安装成功
02. 创建一个home-work文件夹
03. cd  **home-work   切换到当前文件夹下 回车
04. 创建两个文件，app.js  index.html
05. git init  初始化一个空的仓库
06. git config --global user.name 'xieerduos'  全局配置git，配置用户名
07. git config --global user.email '1454598684@qq.com'  全局配置git，配置email
可以随 时改用户名和email，用相应的命令就可以了
08. git  add index.html 当你按回车的时候就添加到相应的队列里面去了
09. git status   查看文件是否被添加呢   按回车后，会看到两个文件，一个被添加了（绿色）一个没有被添加的
 (use "git rm --cached <file>..." to unstage)  如果你想删除，上传的文件的话是，使用git rm --cached <file>
10. git  rm --cached index.html 回车，将index.html从上传队列里移除（remove）
11. git status  查看状态
12. git add *.html  上传某一类文件
13. git status  查看状态
14. git rm --cached index.html  从队列中移除index.html
15. git status  查看状态
16. git add .   将所有的文件提交到队列里去
17. git status  查看状态

18. 把home-work里面的文件打开（sublime，vscode）
19. 给index.html添加内容
20. 返回终端输入：git status
21. 发现有一个“ modified:   index.html ”， index.html发生了修改的意思
22. git add .   再此把所有的文件添加到队里里面
23. git status  查看状态

24. git commit  提交确认
25. 回车     回车之后会进入一个页面，让你备注当前你所提交的信息
// 就是说，现在你写完了，你要把文件提交到你的仓库里面，你要备注一下，提交的是什么，让别人也知道，你提交的是什么
26. 在页面的顶端写入备注信息，
27. Ctrl + C   然后在输入  :wq  退出
28. 你会退回终端，然后发现 
// [master (root-commit) 40d4971] first commit
//  2 files changed, 12 insertions(+)
//  create mode 100644 app.js
//  create mode 100644 index.html
// 说明这两个文件已经被提交上去了

// 29.git status  查看状态，看看有没有提交上去（终端出入，“nothing to commit,working tree clean” 意思是你的所有文件已经被添加到本地仓库里面去了。
// 30.进入app.js 输入console.log('hello world') 然后保存  (意思是修改app.js文件)
// 31.git status  发现 modified： app.js    意思是app.js已经被修改
// 32.git add .   将所有文件添加到队里里面去
// 33.git status  查看状态
// 34.git commit -m 'changed app.js'  这句话的意思其实是，做了我们之前的两步
// 第一步是：git commit   当你输入它的时候，它会跳出来一个备注的界面，你需要去备注对应的信息
// 第二步是：备注信息呢就是 'changed app.js'  
// 这样子写呢，就是一次性提交并且备注了  然后按回车
// 终端输出：
//  [master 9a42317] changed app.js
//  1 file changed, 1 insertion(+)
// 意思是，修改了app.js  1个文件发生了变化

// 以上的就是把两个文件提交到我们的本地的仓库里面来了！

// 以上呢，是操作本地的git仓库
// 以下呢，会分为四个部分来说
// 1.如何使用git忽略不想上传的文件
// 2.分支的使用
// 3.主线及分支的合并
// 4.操作远程仓库

// 第三：主线及分支的合并，
// 第四：我们要把本地仓库的内容推送到远程仓库里面

// 35.在home-work文件夹下面创建一个文件log.txt  一般你的.txt文件是不需要上传到git仓库里面去的
// 36.在log.txt中随便写入点东西  ，现在想要做的是忽略这个文件
// 37.git status   查看状态，提示，log.txt文件需要上传，那怎么忽略呢，往下看
// 38.在当前的文件夹下，创建一个文件  .gitignore 必须是这个名字，意思是忽略一些文件，或者文件夹
// 39.如果你想忽略那个文件，就在.gitignore中写入文件的名字或者文件夹的路径
// 40.git status  此时会发现只有一个.gitignore，并没有log.txt，一般情况下是应该有两个的，一个是.gitignore，一个是log.txt。由于已经忽略了这个文件，所以不要显示出来

// 以上就是忽略，这个文件的例子，以下再来一个例子
// 41.git add .   把.gitignore提交上去
// 42.git status  查看，已经提交上去了
// 43.有时候我们不想提交上去的不一定是某个文件，还可能是某个文件夹，
// 44.在home-work下创建两个文件，dir1、dir2

// 45.在dir1和dir2中，创建一个文件，app1.js,app2.js，并且写入一句话congsole.log("dir1"),congsole.log("dir2")
// 46.如果你想忽略dir1，就把dir1的路径放到.gitignore里面去
// 47.在.gitignore里面写入  
//   log.txt
//   /dir1
// 这样会把dir1文件夹和log.txt都忽略掉
// 47.git status  此时，提示，只有一个dir2，需要我们去add
// 48.git add .
// 49.git commit -m 'another changed'  这样子呢把dir2也已经上传到我们本地的git 仓库里面去了

// 50.接下来是介绍怎么去创建一个分支，如果你想创建一个分支的话，
// 你可以通过  git branch  命令来创建
// 分支的好处是：它不会影响当前主线的这些文件，也就是说，
// 在真实的项目当中的话
// 我们会有一个最主要的项目，这个项目是没有任何问题的时候，才会去使用它

// 如果说分配给你的任务，比如说做一个登录的页面
// 这个东西，你还没有完全做成功之前，需要在你的分支里面操作
// 因为你在自己的分支里面操作，不会影响你主线的项目，
// 待你的分支完全好使了之后，你才可以把它放到你的主线项目里面来
// 所以现在先创建一个分支，大家通过最终的效果来体验一下

// 51.git branch login    login是一个分支名，是你自己起的
// 52.git status  看一下当前的状态
// 提示：
//      On branch master
//      nothing to commit, working tree clean
// 意思是，现在是在一个master，已经有的主线，然后说我们没有需要commit的
// 所以就不需要commit的，也不需要添加
// 我们已经创建完了，之后怎么切换到我们所创建的分支呢、往下看
// 53.git checkout login  切换到分支名字为login的分支下
// 提示：Switched to branch 'login' 意思是当前你已经在分支里面了
// 54.那么在分支里面就可以做你自己的事情，
// 比如说：我们可以创建一个对应的文件，文件为login.html
// 并向里面写入内容，然后在index.html里面也写入一句话

// 55.git status
// 56.git add .
// 57.git commit -m 'login form'  
// 58.终端提示：
//         [login 7b2f6bb] login form
//         2 files changed, 14 insertions(+)
//         create mode 100644 login.html
// 说明已经把上面两个文件提交到本地仓库里面去了
// 59.git status 
//  On branch login
//  nothing to commit, working tree clean
// 上面的意思是在分子login上面没有什么可提交的了
// 现在来确认一下，在分支当中所做的操作，是否会影响我们主线里面的操作
// 60.git checkout master  切换会主线，这个是给我们预定好的，必须要这么写
// 然后你会发现，目录下的的login.html不见了，
// 然后在去查看一下index.html里面修改的内容，明明是修改了的，然后也没有了，
// 所以在你的分支里面所操作的内容，跟你的主线，不会有任何的影响
// 61.git checkout login  再切换到分支login
// 会发现，login.html又出现了，index.html修改的内容又出来了
// 这就是怎么使用分支

// 接下来说的是，你如果在你的分支里面，已经把你的代码写好了，
// 我们需要在主线里面，把你分支里面的代码合并起来，这样就成了一个完整的项目
// 合并的话怎么操作呢?
// 首先回到主线里面，分支可以有很多个，但是主线只有一个
// 62.git checkout master  回到主线master
// 63.git merge login 
// 提示：
//       Fast-forward
//       index.html |  2 ++
//       login.html | 12 ++++++++++++
//       2 files changed, 14 insertions(+)
//       create mode 100644 login.html
// 意思是：分支和主线已经合并起来了，主线就已经拥有了分支里面的内容了
// 
// 64.接下来讲的是，怎么跟远程仓库进行对接
//    (1).浏览器输入：https://github.com
//    (2).然后Sign up for Github  其实是注册GitHub账户
//    (3).然后就是登录
//    (4).登录之后，或许会有一个引导的，不过你可以忽略
//    (5).把鼠标移到右上角的“+”那里，然后 点击New repository  其实就是创建一个仓库的意思
//    (6).我们在本地仓库，已经拥有了相对应的文件，我们需要把本地仓库的文件推送到远程仓库里面来，
//    (7).在Repository name下的输入框里面就可以创建你的仓库的名字（需要跟本地的仓库名字一样，一般是my name形式），如果输入了仓库名字，然后后面是对勾的话，说明这个仓库名字是可用的。现在输入home-work
//    (8).下面有两个，一个是Public（免费的），一个是Private（花钱的）
//    (9).Initialize this repository with a README   意思是，是否初始化README ，当然啦，你可以选择和不选择。现在我是不选择的
//    (10).点击Create repository  按钮
//    (11).然后会创建出一个仓库，名字叫做home-work
//    (12).里面有两个部分，
//       第一：…or create a new repository on the command line
//          如果你是还没有一个仓库的话，你需要在你的本地，进行一下步骤
//          echo "# home-work" >> README.md
//          git init
//          git add README.md
//          git commit -m "first commit"
//          git remote add origin https://github.com/xieerduos/home-work.git
//          git push -u origin master
//       
//       第二：…or push an existing repository from the command line
//          如果你已经存在仓库了话，直接使用一下两行代码
//          git remote add origin https://github.com/xieerduos/home-work.git
//          git push -u origin master 
// 65.git remote  查看有没有git remote地址，（remote是远程的意思）
// 66.如果输入git remote没有任何的输出的话,
//    就复制上面的地址:git remote add origin https://github.com/xieerduos/home-work.git
// 67.git remote add origin https://github.com/xieerduos/home-work.git
// 68.git remote    如果输出origin,那么表示已经联系上了.
// 联系上了之后，我们要push，也就是，复制上面的第二的第二行代码：git push -u origin master 
// 69.git push -u origin master 
// 如果是username https://github.com : xieerduos  回车，然后再输入密码。就可以了
// 恭喜你！走到了这一步
// 注意注意，前面有坑有大坑！！请看下面

// 70.当你git push -u origin master 会有提示：请求失败
// 第一：打开Git Bash，在开始菜单中有一个Git文件夹，点开选择 Git Bash
//      $ cd ~/.ssh //检查计算机ssh密钥
//      如果没有提示:No such file or directory 说明你不是第一次使用git,执行下面的操作,清理原有ssh密钥
//      $ ls 
//      config id_rsa id_rsa.pub known_hosts 
//      $ mkdir key_backup 
//      $ cp id_rsa * key_backup 
//      $ rm id_rsa *
// 获得密钥：
//      ssh -keygen -t rsa -C "xieerduos@1454598684@qq.com" // 填写email地址，然后一直“回车”ok，xieerduos和后面的邮箱都是是我的github的名字和邮箱，这里写你们自己的
//      打开本地..\.ssh\id_rsa.pub文件。此文件里面内容为刚才生成人密钥。
//      4.登陆github系统。点击右上角的Account Settings --->SSH Public keys ---> add another public keys
//      把你本地生成的密钥复制到里面（key文本框中）， 点击add key 就ok了
//      5. 接着打开git ，测试连接是否成功
//      $ ssh -T git@github.com
//      如果提示：Hi xieerduos You've successfully authenticated, but GitHub does not provide shell access. 说明你连接成功了
// 第二：把你的本地仓库名字改为（就是文件夹名字）name-name，远程仓库的名字改为：name name  --其中这两个的名字相同的，就是有一个是中间有“-”，有一个中间是空格，记住了！
//      在这里我改的是：远程仓库的名字为home work，本地仓库为home-work，
// 第三：
//      $ git remote add origin git@github.com:xieerduos/home-work.git    // 连接远程github项目   
//      $ git push -u origin master    //

// 已经解决了！

// 71.到GitHub，home work仓库中，刷新，就会发现，你已经有用了跟本地目录一样的那些文件了
// 72.touch README.md    这个命令是在Git Bash上面去打的，也可以在文件下直接创建一个README.md文件
// 73.到README.md中，写入#myapp this is git ....   #开头是.md的语法
// 74.git status  查看
// 75.git add .  把README.md给添加到队列里面去
// 76.git commit -m 'README.md changed' 将README.md提交到本地仓库，并且备注
// 77.git push   将本地仓库push到远程仓库中
// 在这里，就不需要进行连接了，直接使用push，就自动找到对应的仓库。
// 78.回到GitHub远程仓库，进入home work仓库，刷新，在底部，你会发现，显示着你刚刚在README.md的内容，你可以在README.md里面写一些对你的项目的描述，其实其他人的GitHub里面也会有一些，对当前项目的介绍什么的，当前项目怎么启动等等！
// 79.然后可以做的是什么呢？克隆一个仓库！
// 如果说，你想把远程仓库内容克隆到你的本地的话，在仓库右边有一个绿色的按钮，叫Clone or download。
// 单击按钮，会出现一个地址，再点击地址后面的按钮，拷贝一些地址。
// 80.拷贝完了之后，回到终端（Git Bash）
// 81.在桌面（或者其他地方）创建一个文件夹，叫myapp2（名字自己起，英文的），
// 然后在终端（Git Bash）上面输入cd  然后再把myapp2拖到终端来  然后回车
// 82.git clone https://github.com/xieerduos/home-work.git  地址是你刚刚在GitHub复制的那个地址。如果复制不了，那么就 手动输入吧
// 83.打开myapp2发现你就有了一个一模一样的仓库（home-work）了
// 这就是怎么去克隆

// 以上讲了，git以及git常用的命令

// 以下讲的是，如何使用GitHub给我们提供的客户端，进行数据的存储，本地的仓库存储，以及远程的仓库存储。

// 84.GitHub是什么？
// GitHub是借助Git管理代码的平台
//      1.Git是代码管理工具
//      2.GitHub是基于Git实现的代码管理平台，Github是一个平台，需要做的是存储对应的仓库里面的代码，
// 85.GitHub的使用流程
//      1.在GitHub官网创建账号
//      2.创建远程仓库（用来存储代码）
//      3.安装GitHub客户端
//      4.登录客户端并克隆仓库
//      5.在本地仓库中存储数据
//      6.提交数据并备注信息
//      7.同步本地数据到远程仓库
// 86.安装客户端  到官网去下载！ 地址：Desktop.github.com
// 87.进入 https://github.com 创建一个仓库，这个是特别的仓库
// 这个特别的仓库，就是你的Owner是什么，你特别仓库的名字前面的那部分，就是什么
// 然后就是现在我的是Owner是xieerduos，这个仓库名呢就是xieerduos.github.io
// 使用这个仓库的好处是什么？可以使用它作为一个服务器，可以把你的作品，展示到对应的服务器上面来。
// 写好仓库名字后，单击最下面的绿色创建按钮，Create repository
// 88.回到GitHub客户端  当然有登录的状态或没有登录，那么登录就是了
// 89.找到Clone a repository  按钮，并单击     我第一次打开是，在页面的左边
// 90.将你的GitHub仓库克隆下来   可以全部克隆下来，也可以找到你想要克隆的仓库。
// 91.现在克隆刚刚创建的那个特别的仓库，选中-->单击下面Clone按钮
//    它会把远程的仓库，克隆到本地下面来。克隆的时候可能会让你选择地址，就是你把克隆后放到哪里的意思。
// 92.当你单击后，发现什么都没有，也没有想老师视频上的那样，但是，在右边有一段话，叫 
// No local changes，Would you like to open this repository in Explorer?
// 意思是本地仓库没有变化，您想在资源管理器中打开这个存储库吗？
// 93.单击open this repository即可打开这个仓库，（其实就是一个文件夹）
// 94.（这一步多余，可忽略）打开终端（Git Bash）并输入cd加空格--->返回上一个文件夹(就是刚刚open this repository打开的那个文件夹的上一个文件夹)--->选中xieerduos.github.io文件夹（你就是选中你对应的文件夹）--->然后拖到终端（Git Bash）里面 ---->回车
// 95.找到刚刚保存到本地的那个特备仓库，默认是在，文档--->GitHub--->xieerduos.github.io(名字可能不一样，选中你的仓库名)---->用vscode打开这个文件夹，并且在里面写入一个文件index.html，并且在html基本结构里，写入一段文字 "this is 我的作品！"
// 96.这时候，你打开GitHub客户端，你会发现，index.html在里面了！
// 然后在客户端的左侧有一个提示，" 1 changed file "
// 97.在客户端的左下角有一个，Summary（概括的意思）输入框，这个是必须写的；下面有一个Description（形容，描述，选填）文本域。在Summary中写入"我的作品"
// 98.单击Commit to master   意思是，把这个这个index.html文件提交到本地仓库里面去  
// 99.单击后，客户端，右边的显示会消失，左边也显示为“0 changed files”
// 100.然后单击客户端左边的一个上面菜单栏的，Push origin按钮单击
// 单击后，会把文件推送到，远程的特殊仓库xieerduos.github.io中
// 101.打开这个GitHub.com中的xieerduos.github.io仓库，刷新就可以看到我们刚刚同步上来的index.html文件了

// 102.刚刚我们做的这个特别的仓库，有什么特别之处呢？
// 103.它的特别之处就是我们可以把它当做是一个服务器。
// 104.服务器的地址是：https://xieerduos.github.io/  (你的就是你对应的仓库地址了，这个是我的)
// 105.在浏览器地址栏输入：https://xieerduos.github.io/ 回车，就可以看到了，“ this is 我的作品 ”！  这个其实就是，我们刚刚写的html。这样子，我们可以把我们的作品，上传到GitHub仓库里面，也可以分享给其他的好友们。
// 106.如果你有多个作品的话，那么你只需要在特殊的本地仓库里面创建文件夹，然后在地址上面加上那个文件夹的名字即可。
// 107.比如我现在特殊的本地仓库里，创建一个project2，并且在里面写index2.html，内容也是index2.html。，
// 108.GitHub客户端，在Summary写入“作品index2”，然后按下 Commit to master 按钮，然后在右边上面的，Push origin按钮单击，将这个文件推送到远程仓库中
// 109.我在地址栏上面写，https://xieerduos.github.io/project2/index2.html 就可以显示页面了

// 以上是，可以本地仓库的使用

// 110.现在，我们使用的服务器，是github.io，一看就是github的服务器了，如果我们想要一个个性化的服务器，怎么办？
// 111.自己看视频！恭喜你已经学完了！




// 删除github仓库里面的某个文件夹

//    $ git rm -h
// 用法：git rm [<选项>] [--] <文件>...
// -n, --dry-run                 演习
// -q, --quiet                    不列出删除的文件
// --cached                      只从索引区删除
// -f, --force                     忽略文件更新状态检查
// -r                                  允许递归删除
// --ignore-unmatch      即使没有匹配，也以零状态退出

// 我的操作历史：

// 1     git rm -r --cached  "React版单页面音乐播放器"
// 2     git commit -m "remove new gitignore directory"
// 3     git push origin master   