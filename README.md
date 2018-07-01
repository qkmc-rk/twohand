# 校园二手平台


**开发环境：** IntelliJ IDEA、Atom、Navicat for MySQL
**使用技术：**

 -  Spring+SpringMVC+Mybatis，Maven
 -  JavaScript+Jquery+React
开发人员： 洪国栋、郭跃滨、李昌晋、黄会准、叶昊辛
项目分工： 按照功能进行模块化开发，每人负责的模块要兼顾前端+后台。 
界面展示：

 **首页** 
商品展示页面的首页，即系统的主页面，主页面包括了物品的分类，导航栏，发布商品，登录注册，消息通知，商品搜索栏，以及页面每一分类中显示最新更新的6件商品信息
![首页](https://gitee.com/uploads/images/2018/0701/195803_98d15fbb_1622082.png "QQ图片20180701195738.png")

 **最新发布** 
![最新发布](https://gitee.com/uploads/images/2018/0701/195254_c48d0d19_1622082.png "2)$B6Z{RD{MC]%MEI_W{A2C.png")

 **登录模块** 
　　用户点击主页面上的登录按钮，前台js控制会弹出登录悬浮窗口，填写登录的手机号和密码，点击登录，会请求到UserController，调用其中的loginValidate()方法，将密码用MD5加密与数据库中的加密信息匹配，匹配成功后，将用户信息添加到session会话中，并根据请求头部信息中的Referer跳转回点击登录的页面。 
![登录模块](https://gitee.com/uploads/images/2018/0701/195631_9a8c8526_1622082.png "X%XL(CAE6(JA`JO_J0@10D8.png")

 **注册模块** 
　　在首页或登录框中点击注册按钮，就可以弹出注册框，注册的登录号为手机号码，系统会对数据进行校验，核对正确后可注册并登录。 
![注册模块](https://gitee.com/uploads/images/2018/0701/195718_2f6bfa77_1622082.png "8D5)4[XUTZK}6SF_WBK7_W4.png")

 **登录成功截图** 
![登录成功截图](https://gitee.com/uploads/images/2018/0701/195910_67ac98ff_1622082.png "在这里输入图片标题")

 **个人中心** 
![个人中心](https://gitee.com/uploads/images/2018/0701/195957_c5668a05_1622082.png "在这里输入图片标题")

 **发布商品界面** 
    发布商品信息需要填写相应的商品文字信息，以及上传商品的图片信息。上传图片信息，需要前台传入一个文件类型的对象，根据该对象，取出上传图片的物理路径，将该图片保存到磁盘中，并将新图片的名称返回到前端显示。若图片不合法，将返回不合法信息，提示前台图片不合法。
    将商品信息以及图片信息传到后台，后台获取到session中的用户信息，并对商品设置用户的外键关联，在goods表中，插入商品信息。插入商品信息后，获取物品的id，并对图片设置商品的外键关联，在image表中插入相应的图片信息。之后更改用户的信息，将该用户发布的商品数量加1，并更新分类表中该分类所有商品数量。最后修改session中用户的值。
![输入图片说明](https://gitee.com/uploads/images/2018/0701/200026_218ad08d_1622082.png "在这里输入图片标题")
上传注意事项：像上图一样打开照片后，右下角有3个按钮，分别是上传、删除、放大图片，要点击上传按钮，才能确保照片上传成功，不是打开照片显示了照片就可以了。


 **商品界面** 
在商品展示页，点击商品图片，可以查看商品的详细信息。默认在未登陆状态下，是不可查看商家的信息的，只有在登录之后，才可以查看到相应的商家联系方式。在用户点击商品后，首先请求后台，进行是否登录的一个过滤，然后后台查询出该商品的详细信息，商品的多张图片信息，卖家的信息等，返回到前台显示。 
![输入图片说明](https://gitee.com/uploads/images/2018/0701/200343_fbc4af2e_1622082.png "在这里输入图片标题")

 **商品详情及评论** 
![输入图片说明](https://gitee.com/uploads/images/2018/0701/200413_8f1eac52_1622082.png "在这里输入图片标题")

 **已发布商品界面** 
每个用户，都有自己发布过的闲置物品，在个人中心模块，可以查看曾经发布过的闲置物品，并且可以对相应的物品进行删除和修改操作。
![输入图片说明](https://gitee.com/uploads/images/2018/0701/200518_a922b1e1_1622082.png "在这里输入图片标题")

 **个人信息设置模块** 
　　用户登录成功后，可以进入到个人中心，刚注册的用户，可以在个人设置页面进行完善自己的信息，也可以在此页面修改信息，但是开通时间与手机号码，不可更改。 
![输入图片说明](https://gitee.com/uploads/images/2018/0701/200552_f6c99552_1622082.png "在这里输入图片标题")

 **商品搜索结果** 

　在首页的顶部，添加了一个搜索框，在搜索框中输入关键字，就会请求后台，后台会根据关键字，查询商品表中的name和description，查询出带有该关键字的商品以及对象的图片信息，返回到前台显示出相应的商品信息，例如查询：书，可以查询到书籍的商品，且避免了商品名称中不带“书”字查询不到的错误。 
![输入图片说明](https://gitee.com/uploads/images/2018/0701/200723_445a0e65_1622082.png "在这里输入图片标题")

 **商品分类** 
    系统的主页面，将物品分为了最新发布，闲置数码，校园代步，电器日用，图书教材，美妆衣物，运动棋牌，票券小物等7类。点击分类名，请求后台，后台将数据库中商品为该分类外键的查询出来，将商品信息返回到页面上，页面将跳转显示相应的分类下的商品信息。 
    点击分类后，可实现在该分类下，查询相应的商品信息，在该分类下，同样可以进行模糊查询，只不过是在分类下进行模糊，匹配的是catelog_id，然后在该分类下匹配商品的name和describle，例如在校园代步分类下输入：爱玛，查询的就是校园代步下关于“爱玛”的商品信息。 
![输入图片说明](https://gitee.com/uploads/images/2018/0701/200753_92de7630_1622082.png "在这里输入图片标题")

 **系统管理员模块** 
 **用户管理模块** 
    使用Ant-Design UI实现企业级管理台的解决方案。管理台作为子系统，显示了用户管理和商品管理的功能，下面是用户管理页截图，以表格的形式直观的展示数据，并且支持多条件查询、跳转页面等功能。每行表格都有操作项，包括更新和删除功能。
![输入图片说明](https://gitee.com/uploads/images/2018/0701/201812_f36e5d87_1622082.jpeg "在这里输入图片标题")
    点击修改时弹出对话框，对话框下层有一层遮罩，这层遮罩可以防止在发起异步请求时在页面上进行了错误操作，点击遮罩对话框会消失。更新对话框展示已有数据，并对输入数据进行校验，输入正确出现正确提示符，点击确定发起请求同步到数据库，修改成功后关闭对话框。 
![输入图片说明](https://gitee.com/uploads/images/2018/0701/201906_427daa53_1622082.jpeg "在这里输入图片标题")
 **商品管理模块** 
    商品管理模块同样采用表格的形式，支持多条件查询、分页、查看详细信息等操作，不同的是商品的信息不允许修改但是可以删除。点击商品名可以进入详细信息页面，展示该商品的全部数据。 
![输入图片说明](https://gitee.com/uploads/images/2018/0701/201922_7e7a68a6_1622082.jpeg "在这里输入图片标题")

 **总结** 

 **洪国栋** ：整个项目做下来，深刻的体会到了一个项目的开发流程。从需求分析到项目部署，每一步都是至关重要的，尤其是开发文档，文档使得开发变得更规范，这个项目基本实现了校园二手平台的功能，无法实现线上交易，目前只能做到线下交易，这让买家与买家之间增加了很大的困难。也深刻体会到了一个团队的重要性，缺少了一个模块，整个项目进度都难以掌控。

 **郭跃滨** ：学完了这门课，让我了解了一个项目做下来需要哪些文档，还有搭一个二手平台所需要涉及到的技术，虽然在搭建平台的时候需要了许多技术问题，不过好在在组长的指导下成功的解决了这些问题。

 **黄会准** 
软工实践课一个学期过去了，对比之前毫无任何项目开发经验的我而言，现在对于项目开发的流程与编程有一定的了解。那我就谈谈这门课给我带来的收获吧。
这次项目开发，我学会使用github管理项目开发流程，学会IDEA这款软件的使用方法，而且变得经常逛IT技术社区，像csdn、开源中国以及码云等等。经常去慕课网、网易与课堂等自学java与项目开发知识。我们使用IDEA软件和springboot框架进行开发，开发过程中我掌握了使用Unitis测试各个层。
1.善于使用开发框架
特别是对于我这种毫无开发经验的人来说，不使用框架进行开发是十分困难度的。使用一个合适的开发框架对开发者而言是件十分方便的事，因为我们只要配置好数据库事务和几个xml文件(主要是拦截器)，配置好服务器，然后写好其他各个层的代码与jsp页面就可以了。怎么样？简单不？
2.善于调试代码
经过这次项目开发之后，我发现之前上C++老师要求的代码调试的重要性显示出来，以前只知道代码运行过了就可以，现在知道代码的作用是她能起到我们所要求的功能才行。我现在知道看错误日志，知道如何使用百度解决各种各样的难题。代码调试这个工作最为繁琐，有的bug隐藏的很深不易发觉，比如我之前那个文件上传，就浪费我好长时间。后来才发现Maven没有把我在main文件夹下的uploads/temp文件打包到target文件夹下。这样我只能自己在target下新建uploads/temp目录。但是我根据日志文件却找不到错误的原因竟如此简单。还有一个是html页面加载css文件的问题。因为我们再Controller类中处理请求时会返回一个jsp页面，只有我们将css文件内容放在jsp页面时，jsp页面才会加载css等静态资源。但这并不是一个好办法，为此我们去百度，去问别人找到一个办法，那就是使用css在服务器站点中的路径，路径可以是绝对路径或者相对路径。因为使用绝对路径比较麻烦，我们就通过浏览器的F12下查看network查看请求状态，不断调试相对路径。还有关于unitis测试各个层并不会很麻烦，csdn上有很多教程，并不会很麻烦。
3.学会使用github等开源项目管理平台
在还没用github之前，我们都是使用QQ互传文件的，这样一来，我们的代码同步就有了问题，有时团队中有一个人写了一些代码，另外一个人写了一些代码，这样两个人的版本就不一样了，多个人的话不及时整合项目版本。
4.团队交流十分重要
团队过程中，有一个领导力出众的人十分重要，如果这个人对项目开发有经验更好，团队中有一个禁忌是团队有时候缺工时间过长，有时候却又十分赶。这个是因为团队没有定时开会交流的原因，虽然成立QQ讨论组已经可以很好的进行交流，但我要说的是线下的交流更重要。在这方面，我舍友的队伍做的非常好，我们就稍显不足。他们组几乎每天晚上都会开会，报告进度，交流遇到的各种问题以及将要完成的任务和分配任务的工作。有时候泡出问题很重要，如果一个问题自己在1-2天内无法解决，就应当主动提出来，避免将时间浪费在重复的失败之中。团队的交流大有裨益，因为每个人都有擅长与不擅长的，每个人会遇到的问题都不一样。还有一点是，要充分调动成员的积极性，一个团队只有一个人写代码不是真正的团队，真正的团队要让其成员有事可做，让他知道他的工作对整个团队而言是重要的一部分。一句话，团队要觉得自己被需要才会努力为这个团队工作，如果成员的任何工作都被否定的话，它就会觉得自己是多余的。

 **叶昊辛** 
一开始感觉这门课很简单, 只要队友会写文档,然后把项目交上去就好了。上了之后….发现没那么简单 真的是各种学习首先是git的使用,以前用git只会commit push pull 根本不懂git工作原理 版本回退 冲突解决 出现文件丢失还是重新写。需求说明书就只能自己一路摸瞎边学边写概要(详细)设计说明书等等.. 说实话..这东西和需求书一样,都是需要大把时间去写的，总之整个过程都没有想象的这么简单，做下来还是学到了很多东西，水平有提高，也算是没白做吧。

 **李昌晋** 
团队过程中，有一个领导力出众的人十分重要，如果这个人对项目开发有经验更好，团队中有一个禁忌是团队有时候缺工时间过长，有时候却又十分赶。这个是因为团队没有定时开会交流的原因，虽然成立QQ讨论组已经可以很好的进行交流，但我要说的是线下的交流更重要。在这方面，我舍友的队伍做的非常好，我们就稍显不足。他们组几乎每天晚上都会开会，报告进度，交流遇到的各种问题以及将要完成的任务和分配任务的工作。有时候泡出问题很重要，如果一个问题自己在1-2天内无法解决，就应当主动提出来，避免将时间浪费在重复的失败之中。