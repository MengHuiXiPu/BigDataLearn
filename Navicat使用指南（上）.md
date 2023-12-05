# Navicat使用指南（上）

Navicat的功能非常多，这里为了让小伙伴们一一掌握，分为上下两个篇章具体讲述。

**目录**

- 安装Navicat
- 连接不同数据库
- 创建数据库
- 数据传输
- 导出表结构
- 生成数据字典
- 查找数据或表名
- 生成E-R模型

*注：以上功能无需书写任何SQL代码*

**安装Navicat**

因为工作原因，需要经常连接不同的数据库，这里我安装的是Navicat Premium版本，在公众号后台回复 **Navicat** 即可获取。

安装过程很简单，只要你能看懂中文，不停的下一步，等待安装完成即可。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2xKluMyr9zsylJ1bbEy5kAicNwLkqjO2V3j6G3XFBLhiaozUuKYzLCVkQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



**连接不同数据库**

这里分别介绍Oracle，MySQL，SQL Server这三种数据库的连接方法

**连接Oracle**

在连接Oracle之前我们需要先配置一下OCI文件，具体如下：

点开主菜单里的【工具】——【选项...】,在弹出的对话框中找的OCI选项

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2ayiavVhGWNUtCxzSv7nRAL32mTpAlsHmG6XrhvA5NfV7JIUia6FnBDWA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



这里就要把你安装的oracle的安装目录下的bin文件夹里面的oci.dll文件导入

E:\software\oracle\Oracle_win64\product\11.2.0\dbhome_1\BIN\oci.dll

以上是我的安装目录下的文件，大家根据自己的安装目录不同来导进来

导进来之后就重启Navicat，重启后会自动生效。

重启Navicat后，点击菜单栏的连接，选择Oracle，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2v4ibO1bTE1sICWwbjoGlYjlPrbKGNmCazdqNG3U4SJDY4lNvydb8vGA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

在弹出的对话框中做如下配置，其中连接名可以随意起，然后输入你要连接的主机名或IP地址，最后输入账号密码。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO26DXvmnuAFhema70Vibkj2nhLc13TEpb2SwxMibrVuY9ECoP4BudbRf0A/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

如果你是使用DBA角色登录的，还需要点开高级选项卡，将角色选为DBA

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO225C85ic0Bd8oYibzpBoHLKtmog0ZBdlib7Pd8grxHDIia7aNwEVdfw46uA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

配置完了以后，我们可以点击连接测试

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2pBzAsdJSbnWUI9La2k8icmAKIbnMWpOMicy9FsgFO1CdKCiaC2p3OqUOA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)这样Oracle的连接就配置好了。



**连接MySQL和SQL Server**

MySQL和SQL Server的连接相对比较简单，只需要输入主机名或IP地址，账号密码即可，具体如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2HxIZHHUhGKML0TC1mgA7djpa5KZ2cqyJyrW5HUAtr9xIwxAJBWxobg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2UzsMibLp6NUbiaAE5dNa09XeOjh61qyCmUib1uRzpy8p1PnwZd3FMuUxg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

配置好后，点击连接测试，在弹出连接成功窗口就表示我们配置好了。

数据库连接成功后，下面是各个功能的介绍，我们以SQL Server数据库作为案例来介绍各个功能的使用。



**创建数据库**

右键我们刚新建的数据库连接——选择【新建数据库...】即可开始创建数据库了。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO25lWoNb7icSiaocd6c07JMQRVdvqrXHpnPpmOWMkEXk5lSUPhTxCvE3Fg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

可以根据你的要求来进行配置，配置完以后，还可以在【SQL预览】看到完整的SQL代码：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2f6LfOqSt2tKhHUhxV089tAicnqGw6gQr1ic6JpNzic21UDxVbicm2pul5g/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



**数据传输**

数据传输，顾名思义就是将数据从其他地方传输到当前数据库，例如我们将SQL_Road数据库中的数据传输到刚才新建的Test数据库中。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO29JIouv6OTsvv1tVHEARMD95v6JjKVnvJ2Cw07xzqUAOPp9ktxpNueQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

右键刚才创建好的Test数据库，在弹出的选项中选择【数据传输...】，在弹出的窗口中我们配置源数据库为【SQL_Road】,目标数据库配置为【Test】，这样就可以将SQL_Road中的对象传输到Test了，支持传输的对象包括：表，视图，函数和存储过程，具体如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2a5ovyOCg7icHWslZj0ZH0icOZG0GG2zF5McQWlWxXhb0h7IH8ScszhyQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

点击开始即可开始进行数据传输，传输效率还是很快的，即使你的数据量很大，也可以使用该方法进行数据传输，这里使用了不到2秒钟就将整个数据库对象迁移到新的数据库中了。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2gYlkicBOLCHXSicuics171YBiaBM06vu5TsoxFD1v8tMiatk27AFnl8icDBw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



此外如果你想导出整个数据库中的对象到文件，也可以使用该方法，只需要将方式改为文件即可，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2dKibsOAkMktKzv4RcEnGCzF21WvhA8u23aO8mxQoXNGpbLRXkjrrasw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

如果你想自定义导出的内容，可以点击该窗口的【高级】选项进行自定义配置，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2ibkdpgmia7AP9ciadmUt0kIpKZHJWBicQibibicdibEtaZFkHcicEGtjG1OSUCg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

配置完成后，点击开始，就会将你选择的数据库对象以脚本的形式导出到文件中。



但是数据传输到文件有个不足的地方，就是会将数据记录也会一并导出，而很多时候，我们其实只需要表结构，那么我们可以使用下面的这个功能。



**转储SQL文件**

双击打开数据库后，我们右键架构名dbo，在弹出的选项中选择【转储SQL文件...】，这里还有两个子选项：【结构和数据...】和【仅结构...】，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2klrr7KbWlHjd8oVYVaFhibky2ywFHxDfGbU0SNr80OElzF5bTVOor1g/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

他们的区别就是一个有数据记录，一个没有数据记录，如果你只要数据结构可以只选择【仅结构...】，这样就可以大大节省导出时间了。



**打印模式/数据字典\**生成\****

做数据库仓库往往面对的不是几张表，往往是成百上千张数据表，该怎么维护对DBA是个非常头疼的事，如果有个数据表结构或数据字典之类的就非常完美了。

打印模式可以**完美的生成所有表的数据表结构**的。这里我们选择表数量较多的数据库ReportServer。右键dbo后，选择【打印模式...】，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2NIZlTicjuVONVpYrhO0W1IqAeicswxic28stRoicXeJokqNTBNSQ3L0zWQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

可以看到右侧窗口里面出现了所有数据表的表结构，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2TvxbdBAlYHmoILKSDia33M0MIm0IAghtK3LXibzq5icU19hqlFYkESx0w/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

足足有10页之多，我们点击左上方的【打印】，将表结构打印成PDF文件，就可以得到一份非常完成的数据字典了，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2aud0pqYSgMzwR3nXRMTNGibYQP3zXkCDrbTEU8UhTKDUhwZ2UDZxrSA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

内容中主键和索引也有仔细的标注出来，其中**P代表主键**，下面的**index表示索引**。

这个功能绝对是一个神器！



**在模式中查找**

这个功能主要用来查找数据或结果，当你需要从当前数据库中查找数据记录或对象中包含某些字符时，可以使用该功能，具体如下：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO26F4rBdtKPq3pM6kk4v0iboN54ExFSJ6P0A8JrFI9x7Aj1zEICJeYw3Q/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

在弹出的对话框中，我们查找pre的结构，就可以将当前数据库符合要求的的所有对象都查找出来，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2zfWey0meibpxuwyU8ljtT6r0JIvHybx1e5rCDeAHwty4T2PIEKdQ1uw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



**逆向模式到模型**

这又是一个神仙技能，谁用谁知道，右键dbo在弹出的选项中选择【逆向模式到模型..】,如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2gqmyJ95SwfRD1sZgybhd30aOiaV4LFDDSSKG7icQyHRGbTicMvBSqYjMQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



它可以**将当前数据库中创建的所有表，以E-R图的模型清楚的告诉你每个表之间的关联关系**，包括主外键，表结构，关联关系等，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2uQjNXTMRT6dVMkyT4tsO8Bb1CnibJgJfWDEePaGpVe8sicmkHdib245iaQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



你以为就这？



还支持**模型转换，模型导出**，说白了就是你可以**将该模型转换成其他数据库的模型**，从SQL Server转换成MySQL，Oracle，Postgresql都可以。点击左上角的三短横，选择【文件】——【模型转换】，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2cyYKRyxc5KAibxWfnU2zWdvUn7wAicn2lxZCBSP8mibaOaiaUbW9TzWn9w/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



在弹出的对话框中选择你要转换的类型，比如我们想转换成MySQL 5.6的，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2x6TSHrBrmkymXceib25CkBfqVibGJlYibS0PL6VpSrOBPiacP71D1iciaBHw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

点击确定后，即可将当前的SQL Server模型立马转换成MySQL 5.6。给大家看下对比效果：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2BUAibtGeIM6N5WXroknLPhTjT4k0r9EaZA8QRgCKzsnnUHsfqict08Tw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

SQL Server模型



![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2ImacDMUrYmibib6ZwhWa5hSwhtVXIhEUia6z4XxSz6chIVaeTzxmQcicuw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

MySQL模型



转换成功后可以直接将转换后的模型导出成对应的SQL。

点击【工具】——【导出SQL...】，如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2SmPTTmH3LNPNNlmst71wAL7cpjlJuicBexVXBLh230wCzz2j3PGfvBg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



选择导出位置，点确定即可，导出的SQL文件里面就是MySQL的建库代码了。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2pvSqyJrD6aqeYmPh2lrIt56UXRL4RKyxzukKiaJ8GvaE2JGyjrKZx6A/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)



能导出肯定就可以打印，同样如果需要将模型文件保存，也可以导出为PDF，PNG，SVG等格式，但是建议打印成PNG图片格式，因为PDF会分页，导致模型不完整。



![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2v0WVtdIJS4Qnj98H6rZwSic0mpKNvY4ML8OQEb4S5Y1cFk7icCmctdnA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

打印出来的图片如下：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qEuaqnkFyFSumPrJqFyURO2VXiacibexrSpbeY1Y7kANuyIKGGobrsFNTiaolsaEMXRaDt8kXdeoibNLA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)