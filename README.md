-------------------------------update 19.12.17-----------------------------------------------------------------------------
sql 脚本不上传的吗  下下来怎么用
-------------------------------update 19.12.17-----------------------------------------------------------------------------



-------------------------------update 18.12.10-----------------------------------------------------------------------------

pom.xml对于部分机器可能存在build没有配置导致override报错，需要加入：

```
<build>
        <finalName>educational_evaluation_system</finalName>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.6.0</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                    <encoding>utf8</encoding>
                </configuration>
            </plugin>
        </plugins>
    </build>
```

同时由于没有idea配置文件，可能会出现导入后tomcat文件运行后不成功问题，需要
Artifacts中找到对应的Output Layout下的classes的右边的Available Elements先第一个单机右键put into output root解决。
会出现这个错误原因在于确实相关spring包在输出位置。

author: yaque
time: 2018-12-10

-------------------------------update 18.12.7-----------------------------------------------------------------------------

&#160; &#160; &#160; &#160;我先背一口大锅= =mybatis这边炸了都是我搞的，现在bug已经解决，实测了一次insert完全ok。

&#160; &#160; &#160; &#160;然后整体代码位置也是我的锅，写的不好，现在已经调整成比较正常的架构，但是myeclipse直接使用pom.xml加载
maven项目的时候还是会和目录有点不同。之后代码只存在源码，与IDE相关的一律不上传。大家上传的时候也注意不要上传IDE的内容，只用上传源码
即可。

&#160; &#160; &#160; &#160;简单解释一下架构：

&#160; &#160; &#160; &#160;src/main是项目源，接下来3个文件：java、resource、webapp。java里面就是包了，里面全部是java代码。
resource主要是各种配置文件（除了web.xml），其中mapper文件里面是mybatis的mapper.xml文件。webapp就是web或者说webroot文件夹，
里面内容不解释了。

&#160; &#160; &#160; &#160;关于mybatis有一点：如果对于实体类有修改，一定要跟我说一下，因为需要在数据库、mybatis这边进行很多修改，
如果不太熟悉mybatis可以私聊我（最好QQ）让我去修改一下。如果熟悉mybatis可以直接修改，但是一定注意不要有bug。

&#160; &#160; &#160; &#160;如果在写代码的时候，需要一个对数据库操作的方法，例如：写学生注册的同学需要insert方法，那么如果熟悉mybatis
就不需要多解释了，如果不太熟悉还是联系我，或者找比较熟悉的同学，帮忙写一下这个逻辑，确保能够使用。

--------------------------------------------------------------------------------------------------------------------------
# 1 模块分配
&#160; &#160; &#160; &#160; 就是群里的截图，可以调整。

# 2 本地项目
&#160; &#160; &#160; &#160; down下来以后idea应该是能直接导入的，但是myeclipse可能会需要一些转换。暂时先试一下在本地配置好项
目，之后应该能GitHub上只保存源码而不包括IDE的配置文件。

# 3 数据库
&#160; &#160; &#160; &#160; 在VPS上，MySQL 5.7。

# 4 controller
&#160; &#160; &#160; &#160; 按照之前讨论的，谁负责相关模块，具体的路径就谁在controller部分添加。

# 5 service
&#160; &#160; &#160; &#160; 这一部分，整体不推荐改变，关于接口中描述的形参列表以及返回值，有不太明白的最好先私下联系，确认以后
再进行修改。方法的增删同理，先确认在修改。

# 6 本地测试
&#160; &#160; &#160; &#160; 没有bug再上传！

# 7 前端后端规范
&#160; &#160; &#160; &#160; 前端需要写好表单之类的，先把css写好，数据随便写。后端同理，测试的时候随便写个html先测试。在最后再
统一合并。

# 8 dao
&#160; &#160; &#160; &#160; 如果需要对数据库进行操作，而dao包内相关mapper接口并没有这个方法，可以直接添加这个方法，同时联系我，
我会尽快添加mybatis的SQL语句。可以自己添加SQL语句映射关系，前提需要自己测试正确。

# 9 其他
&#160; &#160; &#160; &#160; 还有其他注意可以商量之后增加。推荐写在README.md，这样方便阅读。
