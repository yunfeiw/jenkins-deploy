## linux 下部署 jenkins

### 安装

    > jdk8

    1、下载 [jdk 8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html) jdk-8xx-linux-xxx.tar.gz

    2、上传至服务器解压到 usr/local/java 目录下

    ```
      tar -vzxf jdk-xxx-linux-xxx.tar.gz -C /usr/local/java/
    ```

    3、添加环境变量

    ```
      vim /etc/profile
    ```

    添加以下内容

    ```
      # Java Path

      export JAVA_HOME=/usr/local/java/jdk1.8.0_241
      export CLASSPATH=$:CLASSPATH:$JAVA_HOME/lib/
      export PATH=$PATH:$JAVA_HOME/bin

    ```

    重新加载环境变量

    ```
      source /etc/profile

      java -version
    ```

  > jenkins

  ```
  sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
    
  sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
  
  yum install jenkins

  ```
  
  完成后运行 <font color='yellow'> service jenkins start </font>

  出现异常信息

  <font color='red'>Job for jenkins.service failed because the control process exited with error code</font>

  原因：Jdk地址错误

  解决：配置jenkins信息

  ```
    vim /etc/init.d/jenkins

  ```

  ![1](https://img-blog.csdnimg.cn/20190423170400340.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1ODY4NDEy,size_16,color_FFFFFF,t_70)


  重新运行 service jenkins start

  访问 http://你的IP:8080

END
