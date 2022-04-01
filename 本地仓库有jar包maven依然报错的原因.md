### 问题描述：

本地Maven仓库里面有所需jar包但是依然报错；

### 原因分析：

找到本地仓库后发现里面有一个 ```_remote.repositories``` 文件

![image-20220401185559354](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220401185559354.png)

问题在 ```_remote.repositories``` 

```>nexus``` 说明这个依赖是从私服中下载下来的，而此时我是连不上私服的，所以会有 lastupdate 后缀的文件出现，但是下载不到。

查看正常的 ```_remote.repositories``` 文件是 ```>central=``` 这代表从远程仓库下载。

![image-20220401185924114](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220401185924114.png)

### 解决办法：

将报错依赖 ```_remote.repositories``` 中的 ```nexus=``` 改成 ```central=```

**注意**：这个方法不使用所有的情况，只有确定本地已经真正有了依赖的jar包才行，否则要去尝试中央仓库的URL或者更改依赖包的版本等其他方式解决问题；