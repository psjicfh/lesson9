#lesson9笔记

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


