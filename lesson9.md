

###git revert
作用是修改垃圾文件，即：假使在版本2的基础上做了版本3，并且已经push到远端服务器上。现在发现版本3是个垃圾修改，若想还原版本2的内容，“git revert HEAD”即可还原！
但现在作版本并且要push上去的是版本4，即中间两个版本均是垃圾版本！（注：若错误的执行了“git throwh”, 则必须接着执行“git pull”然后在“git revert HEAD”）

    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ touch trash
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git commit -a
    Aborting commit due to empty commit message.  //作版本的时候要写东西滴！
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git push
    Everything up-to-date                //此错误是因为上句的缘由

    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git commit -a
    [master 4dc5d93] jkdla;
    1 files changed, 1 insertions(+), 0 deletions(-)
    create mode 100644 trash  //此次才成功
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git push

    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git revert HEAD
    Finished one revert.
    [master 5b47b22] Revert "jkdla;"   //注：此时直接做了版本
    1 files changed, 0 insertions(+), 1 deletions(-)
    delete mode 100644 trash
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git push  //还原了

###版本间的跳转
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git checkout 2a9cdbe8ce5f48fd46e8b950   
                                //这一串16进制数是通过tig查看commit号 其做了一个分支拷贝
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git checkout master//回到原来即：master
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git branch //查看分支名称
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git checkout 2a9cdbe8ce5 -b one_file_stare //给分支取个名字
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git checkout master//回到master
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git checkout one_file_stare //跳到one_file_stare分支
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git checkout master//回到master
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git br -D one_file_state //删除分支名称

###例：播放git.mov视频
    akaedu@akaedu-desktop:~/happycasts$ mplayer git.mov
###与git相似的几个命令
git <=> gitk <=> qgit

###做版本的几点注意
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ mv lesson7.c hello.c
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ ls
    a.out  hello.c  say_three_hi.c  say_three_hi.h  say_three_hi.h.gch  tags
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git add . //跟踪所有文件
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git commit -a -v //显示修改内容
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git push
    （注：执行完后发现仓库中包含了文件夹下的所有文件）
    akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ git rm a.out say_three_hi.h.gch tags //删除多余文件


### which  find locate  grep
### $ which git(或 ls tig ……) //查看命令位置
### $ locate .vimrc(各种文件) //定义文件位置
    $ sudo updatebd(更新数据库) 显示了locate 的缺点
### $ find xxx
    $ find xxx|grep git//查找特定文件夹中的文件   grep:匹配一个字符串
    akaedu@akaedu-desktop:~/work$ find lesson9|grep lesson9.md
    lesson9/lesson9.md   //找到
    akaedu@akaedu-desktop:~/work$ cd lesson9
    akaedu@akaedu-desktop:~/work/lesson9$ find lesson9|grep lesson9.md
    find: 'lesson9': 没有那个文件或目录  //未找到
###任务管理器
    akaedu@akaedu-desktop:~$ ps aux | grep firefox 火狐浏览器
    akaedu@akaedu-desktop:~$ kill 1390 结束进程
    akaedu@akaedu-desktop:~$ kill -9 1390 强行结束
###  akaedu@akaedu-desktop:~$ ls|grep tig(文件夹名) //看看当前目录下有无这个文件夹
###在一个project里面 " xxx times(任意字符串)" 的应用
    akaedu@akaedu-desktop:~/psjicfh$ git clone git://github.com/happypeter/hen.git  //克隆peter自己的一个项目
    akaedu@akaedu-desktop:~/psjicfh/hen/search/curse$ vim README
    akaedu@akaedu-desktop:~/psjicfh/hen/search/curse$ sudo apt-get install libncurses5 libncurses5-dev //要安装两个软件
    akaedu@akaedu-desktop:~/psjicfh/hen/search/curse$ make
    gcc -o xxx xxx.c -lcurses  //生成 "xxx" "-lcurses:xxx.c在库里面的定义"
    即：akaedu@akaedu-desktop:~/psjicfh/hen/search/curse$ ldd xxx
        linux-gate.so.1 =>  (0x009db000)
        libncurses.so.5 => /lib/libncurses.so.5 (0x0058a000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00831000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x009fe000)
        /lib/ld-linux.so.2 (0x00216000)
    安装 akaedu@akaedu-desktop:~/psjicfh/hen/search/curse$ sudo make install
         [sudo] password for akaedu: 
         mv xxx /bin                                   完毕
##例子
akaedu@akaedu-desktop:~/work/lesson7/lesson7-project$ xxx times

say_three_hi.c      2        #define HOW_MANY_TIMES_TO_SAY_HELLO 3

say_three_hi.c      6        for (i = 0; i < HOW_MANY_TIMES_TO_SAY_HELLO; i++)

上面“xxx times”的作用是查找此项目中包含“times”的地方，上面两行即是查找到的项目

按“e”即可跳进程序里面，光标跳到要查找处，按“,f”退出。（这个要设置,f=q! 在“.vimrc”里面）

按“K”查看一些接口函数的定义和使用（此是按ctrl+]或ctrl+t不能跳转）

###更改桌面目录
    akaedu@akaedu-desktop:~$ cd .config
    akaedu@akaedu-desktop:~/.config$ vim user-dirs.dirs
    XDG_DESKTOP_DIR="$HOME/桌面" //改桌面……
###打开多个vim页面 new vnew  窗口间跳换ctrl+ww
