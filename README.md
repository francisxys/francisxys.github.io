hexo
## 一、本地环境部署
安装nodejs和gitbash
切换到hexo根目录后，进行初始化
``` bash
hexo init
```
## 二、安装相关的插件
``` bash
#搜索插件
npm install hexo-generator-searchdb --save
#上传deploy插件
npm install hexo-deployer-git --save
```
## 三、hexo命令
``` bash
#初始化
hexo init
#创建post页面
hexo new post "name"
#清除历史缓存
hexo clean
#生成页面
hexo generate
#本地运行
hexo server
#上传到github
hexo d -g
#上传之前将CNAME和READNE.md拷贝进public目录下
```
## 四、markdown语法
### 插入图片
图片链接后跟图片提示
![Alt text](http://pjakaipln.bkt.clouddn.com/20181210019.png "Francis'Blog")
同样支持html语法，居中显示
<center>
<img src="http://pjakaipln.bkt.clouddn.com/%E6%94%AF%E4%BB%98%E5%AE%9D%E6%89%AB%E7%A0%81%E9%A2%86%E7%BA%A2%E5%8C%85.jpg" width="25%" height="25%" />
</center>

### 添加链接格式
前面为文字，后面位文字所附带的链接
[阿里云产品优惠](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=taqd2wlp)

### 表格模板
限制表格列宽
<style>
/* 第一列表格宽度 */
table th:nth-of-type(1){
width: 11%;
}
/* 第二列表格宽度 */
table th:nth-of-type(2){
width: 15%;
}
/* 第三列表格宽度 */
table th:nth-of-type(3){
width: 17%;
}
/* 第四列表格宽度 */
table th:nth-of-type(4){
width: 57%;
}
/*  ... ...  */ 
</style>

| 服务器 | 新生代GC策略      | 老年老代GC策略 | 说明                                                         |
| ------ | ----------------- | -------------- | ------------------------------------------------------------ |
| 组合1  | Serial            | Serial Old     | Serial和Serial Old都是单线程进行GC，特点就是GC时暂停所有应用线程。 |
| 组合2  | Serial            | CMS+Serial Old | CMS（Concurrent Mark Sweep）是并发GC，实现GC线程和应用线程并发工作，不需要暂停所有应用线程。另外，当CMS进行GC失败时，会自动使用Serial Old策略进行GC。 |
| 组合3  | ParNew            | CMS            | 使用`-XX:+UseParNewGC`选项来开启。ParNew是Serial的并行版本，可以指定GC线程数，默认GC线程数为CPU的数量。可以使用-XX:ParallelGCThreads选项指定GC的线程数。如果指定了选项`-XX:+UseConcMarkSweepGC`选项，则新生代默认使用ParNew GC策略。 |
| 组合4  | ParNew            | Serial Old     | 使用`-XX:+UseParNewGC`选项来开启。新生代使用ParNew GC策略，年老代默认使用Serial Old GC策略。 |
| 组合5  | Parallel Scavenge | Serial Old     | Parallel Scavenge策略主要是关注一个可控的吞吐量：应用程序运行时间 / (应用程序运行时间 + GC时间)，可见这会使得CPU的利用率尽可能的高，适用于后台持久运行的应用程序，而不适用于交互较多的应用程序。 |
| 组合6  | Parallel Scavenge | Parallel Old   | Parallel Old是Serial Old的并行版本                           |
| 组合7  | G1GC              | G1GC           | `-XX:+UnlockExperimentalVMOptions` `-XX:+UseG1GC` #开启；`-XX:MaxGCPauseMillis =50` #暂停时间目标；`-XX:GCPauseIntervalMillis =200` #暂停间隔目标；`-XX:+G1YoungGenSize=512m` #年轻代大小；`-XX:SurvivorRatio=6` #幸存区比例 |

# 写作介绍
## 1，字体介绍
*这是斜体* 或 _这也是斜体_ 
**这是粗体**
***这是加粗斜体***
~~这是删除线~~
## 2，分级标题
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
## 3，超链接
写法：

行内形式：[我的博客](https://xfbxfbxfb.github.io/)
参考形式：[我的博客][1]，有一个很好的平台-[简书][2]
[1]:https://xfbxfbxfb.github.io/
[2]:http://www.jianshu.com/
自动链接：我的博客地址<https://xfbxfbxfb.github.io/>

## 4,列表
无序列表：
写法：

* 无序列表项1
+ 无序列表项2
- 无序列表项3

有序列表：
写法：
1.有序列表项1
2.有序列表项2
3.有序列表项3

## 6，表格
| 表头1|表头2|表头3|表头4
|-| :- | :-: | -: |
|默认左对齐|左对齐|居中对其|右对齐|
|默认左对齐|左对齐|居中对其|右对齐|
|默认左对齐|左对齐|居中对其|右对齐|
