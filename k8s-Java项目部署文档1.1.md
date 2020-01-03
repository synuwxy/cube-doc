## 一、创建分支

从最新分支中新建一个分支（现测试的分支为test，以后可能更换分支名称）

## 二、修改配置

1. 在 application.yml 文件的同级文件夹下新建一个  application-local.yml 文件
2. 将 application.yml 的内容复制到新创建的 application-local.yml 文件中
3. 修改 application.yml 文件
    - 将服务的端口改成8080
    - 将所有的外部服务的IP号改成服务名称
    - 将所有外部服务的端口号改成8080
    - 若有Redis/rabbitMQ/...，端口号不变，host改成redis/rabbitmp/...

## 三、提交到远程仓库

``` java
git push
```

## 四、部署

1. 下载cube客户端（若没有找褚磊要）

2. 配置cube.exe文件的路径到环境变量（因为需要在命令行使用cube命令，若出现配置了路径但找不到命令的情况，可以借助以前配置过的系统路径，比如将cube.exe丢到jdk的bin目录下面）

> 若配置成功 命令行执行命令 cube -h 就可以看到帮助文档

3. 执行命令 cube set -s http://dev.apps.cloud2go.cn/cube/manager

4. 登录 cube： cube login -u xxx(gitlab username) -p xxx(gitlab password)

5. 初始化配置 cube： cube create -r xxx(项目全称 例：ctg-service-factory) -a xxx(项目名 例：factory) -b xxx(分支名 例：test) -n cloudos-dev(namespace 固定值) -p xxx(组名 例：business3) -t xxx(语言 例：java)

6. 启动项目： cube run

7. 查看结果：浏览器访问 http://dev.apps.cloud2go.cn/cloudos/dev/项目名/health (项目名中带 - 的转换成 / )，可查看部署是否成功
