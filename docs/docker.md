OhMyDash支持docker方式安装。使用OhMyDash的docker Image您可以快速体验OhMyDash的所有功能。

#### 前置条件
* 您已经安装了docker在您的电脑上，并正确配置。
* 你拥有一个docker hub的账号，并获得我们的授权。

#### 开始使用

* 第一次使用在*nix上使用

我们只用了Docker的Volume映射来保存用户数据到本地磁盘。例如下面的例子中我们使用本地的/tmp/ohmydash来保存用户数据。这样做的目的是您以后使用新版本的OhMyDash的docker image的时候，仍然可以加载原来的数据。

```shell
docker run -d -p 3000:3000 -v /tmp/ohmydash:/opt/ohmydash/u-data stdatatech/ohmydash /opt/ohmydash/bin/start.sh
```

上面的命令运行成功之后，您可以通过 http://localhost:3000 来访问OhMyDash。 默认的用户名和密码为admin/admin.
Docker版本的OhMyDash提供一个功能有限的Free License。您可以和我们获得联系来获得功能更多的License。

* 停止OhMyDash

您可以通过如下命令来停止OhMyDash

```shell
docker stop <your container ID>
```
您可以通过如下命令获得container ID

```shell
docker container ls | grep stdatatech/ohmydash
```

* 重新启动OhMyDash
  
您可以通过运行如下命令启动

```shell
docker start <container ID>
```
  您可以通过如下命令获得container ID

```shell
docker container ls --all | grep stdatatech/ohmydash
```

* 升级OhMydash

如同第一次运行一样，使用如下命令启动最新的容器:

```shell
docker run -d -p 3000:3000 -p 8080:8080 -v /tmp/ohmydash:/opt/ohmydash/u-data stdatatech/ohmydash /opt/ohmydash/bin/start.sh <your ipaddress> 8080 
```
您需要更新你的license文件，请和我们获得联系来获取您的新的license文件。

#### 使用测试数据

* 下载测试数据

您可以从 https://github.com/stdatatech/dash-examples/releases 下载最新的sqlite数据库文件demo.db.gz。Linux或者Mac下面执行下面的命令解压，Windows上请使用解压工具解压。
```shell
  gzip -d demo.db.gz
```
解压之后您将获得一个demo.db的文件，然后创建sqlite数据源,步骤可[参见](sqlite)

!> 请创建名称为demo的数据源，这很重要，将来导入图表的时候，会根据这个数据源的名称和类型进行自动绑定，这会省去您很多时间。

* 下载图表

您可以到github https://github.com/stdatatech/dash-examples 上下载我们为测试数据创建好的图表并导入进去。 如下图所示:

![Example](dash-example.jpg)

下载完毕之后，解压，您将看到很多json文件，这是您要导入的图表。导入图表见[导入/导出](imexport)