# 前言
  该代码于飞牛社区EWEDL大佬编写 https://club.fnnas.com/forum.php?mod=viewthread&tid=7003延迟启动 修改为延迟重启
  
  在某些情况下，我们可能希望在启动 Docker 容器时存在先后顺序，以确保某些前置条件已经满足，例如等待数据库初始化完成、等待cd2完成挂载后再运行其他容器等等。目前飞牛docker暂不具有延时方面的相关功能，为此笔者写了一个简单的脚本项目来实现这一功能，脚本执行后会按用户要求创建一个服务，并按用户设置对容器进行启用（目前系统更新不会对用户创建的服务做更改），整体操作非常简单！
# 关闭自动启动
在执行脚本前，我们需要确定容器的正确部署，最好自己先运行一次。
对于需要添加到延时启动的容器，我们需要关闭他的自启动功能：
容器UI修改方法如下：

![165052rdsl818lpdxbzm81](https://github.com/user-attachments/assets/a26644f5-89a5-4ed1-9733-b864b0c02440)


Compose部署修改方法如下（该方法修改后请手动构建一次以应用修改）

![165053cuos3ohaoiqnqqoa](https://github.com/user-attachments/assets/4b8ddf23-9b01-46dd-8156-dc2400144121)

# 执行脚本
打开终端，输入一下命令，回车执行：

```bash
 curl -s https://gitee.com/ewedl/fn-docker-delay/raw/master/fndocker.sh -o /tmp/fndocker.sh && sudo bash /tmp/fndocker.sh && rm /tmp/fndocker.sh
```
![165053cbgnggf0niboqiig](https://github.com/user-attachments/assets/fa728bbc-cbfb-4da4-b939-227403b98229)

创建完成后，即可重启查看效果，无需进行其他设置。
此外，后续我们也可以直接对配置文件进行修改，默认位于/vol1/1000/config下，该脚本没有任何限制，完全可自定义，你也可以拿他来做别的事情。手动修改完成后，务必再次授予他可执行权限：

```bash
chmod +x /你的目录/start_docker.sh
```
