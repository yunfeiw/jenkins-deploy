## Window 下部署 jenkins

### |安装

- [jenkins 下载地址](https://www.jenkins.io/zh/download/) ;

- 安装时，采用默认配置即可;安装完成默认访问地址[http://loaclhost:8080](http://loaclhost:8080);

- 可更改 workspace，防止其占用 C 盘空间。

  1. 更改前停止服务 【http://localhost:8080/exit/】

  2. "系统环境" 变量配置 JENKINS_HOME : path;

  3. 重启服务。jenkins 安装包下， 运行 ' java -jar jenkins.war '

### |插件

- init 时选择默认插件即可。

- 构建不同流程的 project，所需 plugin 也不尽相同。位置：Manage Jenkins -> Manage Plugins

- 前端任务构建时需要 NodeJs / Post build Task

- 安装完成后，需要配置 NodeJs 全局信息,便于在项目中使用。地址：Manage Jenkins -> Global Tool Configuration -> NodeJs
  ![1](https://img.wenhairu.com/images/2020/12/29/D9dLu.png)

### |构建任务

- 新建任务时，前端任务类型为 Freestyle project

  步骤 1 General
  ![1](https://img.wenhairu.com/images/2020/12/29/D9oXU.png "1" )

  步骤 2 源码管理

  Gredentials 可选 账号密码 或 SSH

  ![2](https://img.wenhairu.com/images/2020/12/29/D9ky0.png)

  步骤 3 构建触发器

  GitHub hook trigger for GITScm polling

  ![3](https://img.wenhairu.com/images/2020/12/29/D9S6j.png)

  步骤 4 构建环境

  Provide Node & npm bin/ folder to PATH

  ![4](https://img.wenhairu.com/images/2020/12/29/D9c9g.png)

  步骤 5 构建

  ！构建命令在<font color='yellow'>window</font>环境下命令需单独使用

  ![5](https://img.wenhairu.com/images/2020/12/29/D9g0K.png)

  步骤 6 构建后操作

  ！构建命令在<font color='yellow'>window</font>环境下命令需单独使用

  ![6](https://img.wenhairu.com/images/2020/12/29/D9ZWo.png)
  ![7](https://img.wenhairu.com/images/2020/12/29/D9Mj3.png)

### 关联 github

GitHub 准备工作

1、在 github 生成 token；
![1](https://img.wenhairu.com/images/2020/12/29/D9b0I.png)

2、配置 WebHook
![2](https://img.wenhairu.com/images/2020/12/29/D9OYH.png)

Jenkins 工作

1、打开 Jenkins -> Manage Jenkins -> fonfigure system - GitHub 配置
![1](https://img.wenhairu.com/images/2020/12/29/D9VXX.png)
凭证
![1.1](https://img.wenhairu.com/images/2020/12/29/D9THq.png)

2、配置源码管理
![2](https://img.wenhairu.com/images/2020/12/29/D9e8p.png)

3、构建环境
![3](https://img.wenhairu.com/images/2020/12/29/D9BG6.png)

-----
END

