GitHub Pages 及 wiki-in-box 使用教程 
===
2015/5/18 14:41:52

## 前言 ##


我也是刚学会不久，因此把自己的操作过程记录一下，以供参考。如有纰漏请告诉我，谢谢！

## GitHub Pages 的使用 ##


1. **首先注册一个GitHub账户**。<br>之前GitHub学生包的时候我提交了学校的邮箱，想申请高级账户（可以设置代码仓库为私有），但是GitHub不认GZHU，没办法，只能用着普通账号。</br>
2. **在Liunx上安装Git工具包**，或者在Windows上安装GitHub客户端。
	1. 在Linux上安装配置Git工具包<br>参考这个文档：[Ubuntu下GitHub的使用](http://www.pythoner.com/263.html "http://www.pythoner.com/263.html")</br>
	2. 在Windows上安装GitHub客户端<br>在此下载客户端：[GitHub for Windows](https://windows.github.com/ "https://windows.github.com/")</br>
3. **了解GitHub Pages机制**
	1. GItHub Pages官方网页：[GitHub Pages](https://pages.github.com/ "https://pages.github.com/")
	2. 我粗略讲一下
		1. 方法一：新建一个yourname.github.io的仓库，并将网页代码放在master分支。<br>通过访问 yourname.github.io 即可访问到你的页面。</br>
		2. 方法二：新建任意一个仓库，例如仓库名为Example，并将网页代码放在gh-pages分支。<br>通过访问 ourname.github.io/Example/ 即可访问到你的页面。</br>
	3. GitHub Pages支持html、markdown、jekyll的解析。
	4. 我没有涉足网页制作方面，具体的也不懂。
4. **找到合适的GitHub Pages模板**，fork一份。<br>通过搜索“GitHub io 模板”就能搜索到很多。并且GitHub上的[jekyll项目](https://github.com/jekyll/jekyll/wiki/Sites "https://github.com/jekyll/jekyll/wiki/Sites")就给出了很多模板供大家选用。我用的就是Wiki-in-box这款，他不是专门的GitHub Pages模板，他是一款简单的 Wiki 引擎。我是从[小众软件](http://www.appinn.com/wiki-in-box/ "http://www.appinn.com/wiki-in-box/")上面知道他的。关于这个项目的详情可以查看他的[GitHub页面](https://github.com/dmscode/Wiki-in-box "https://github.com/dmscode/Wiki-in-box")。</br>
5. **如何创建自己的Wiki-in-box？**
	1. 首先去Wiki-in-box的[GitHub页面](https://github.com/dmscode/Wiki-in-box "https://github.com/dmscode/Wiki-in-box")Fork一份到自己的仓库（repositories），或者直接下载到本地。
	2. 项目下载到本地之后，默认是在master分支下面的。你可以将项目名称改为上述方法一的形式，并上传。也可以切换到gh-pages分支进行修改。他默认的gh-pages分支下面的文件不知道有什么用，需要将master分支的文件合并（merge）过来。但是，由于index.md重复了，因此直接合并会失败。因此请按照以下步骤操作。
		1. 将代码库下载到本地<br>``$ git clone https://github.com/dmscode/Wiki-in-box.git``</br>
		2. 将代码添加到本地git仓库，其中message可换成你喜欢的提示信息<br>``$ git add .``<br>``$ git commit -m "message"``</br> 
		3. 在GitHub上面创建一个代码仓库（repositories）。
		4. 将代码上传到自己的GitHub仓库，其中username改为你的GitHub账户名，repositories改为你的仓库名。<br>``$ git remote add origin https://github.com/username/repositories.git``</br>
		5. 切换到gh-pages分支<br>``$ git checkout gh-pages``</br>
		6. 由于master与gh-pages分支均有index.md文件，因此要先删除gp-pages下原本的index.md文件再合并分支。<br>``$ git rm index.md``<br>``$ git merge master``<br>``$ git commit -m "merge done."``</br>
		7. 上传gh-pages分支<br>``$ git push origin gh-pages``</br>
	3. 至此操作完毕，几分钟后访问 http://username.github.com/Wiki-in-box/ 即可看到你的网页。
	4. 如果不能访问，可能是操作有误或者是我某些步骤遗漏了，毕竟我是凭记忆写下来的，如果对Linux或者Git不熟悉的话，出现某些问题确实不知道怎么解决。有什么问题的话，欢迎都与我一起讨论。
	5. 给出参考资料：<br>[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html "http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html")<br>[使用 GitHub, Jekyll 打造自己的免费独立博客](http://blog.csdn.net/on_1y/article/details/19259435 "http://blog.csdn.net/on_1y/article/details/19259435")<br>[git 分支 合并](http://www.cnblogs.com/sk-net/archive/2011/07/11/2103282.html "http://www.cnblogs.com/sk-net/archive/2011/07/11/2103282.html")</br>

## Wiki in box 的使用 ##

Wiki in box 的定制与修改基本上属于前端的内容了，但是我对这方面并无涉猎，下文都是我自己试着改出来的。应该会有很多错误以及错误的操作，恳请大家一一指出不吝赐教。
### 修改页面宽度 ###
在main.css中，第34行，body>#main区块最后添加一句 ``width: auto;``即可实现页面宽度自动调整。可以将auto改为相应的数值与单位以实现固定宽度。
### 修改代码高亮样式 ###
在index.html中，第11行，monokai_sublime.css修改为你想使用的高亮样式。
### 修改代码块外观 ###
这个与上面的不同，上面是根据css文件来决定代码关键字的颜色，这个部分是决定显示代码区块的行号以及背景色。举个例子，我使用的是vs.css样式，默认情况下背景是黑色的，很难看，因此还要需要修改main.css文件。<br>在main.css中，第72行，pre区块中，background和color参数注释掉即可。
### 参考资料 ###
一个wiki in box的项目 [my-wiki](https://github.com/dmscode/my-wiki "https://github.com/dmscode/my-wiki")<br>Markdown教程 [Markdown教程](http://wowubuntu.com/markdown/ "http://wowubuntu.com/markdown/")<br>代码高亮js [highlightjs.org](https://highlightjs.org/ "https://highlightjs.org/")</br>
## Wiki-in-box的未解之谜 ##
1. 代码区块的行距如何调整？
2. 文章字体如何调整？
3. 顶部Wiki-in-box字样及背景如何修改？
4. 最新发现，[示例文档](tutorial)中的代码样式怎么这么奇怪？


----------
END OF DOCUMENT