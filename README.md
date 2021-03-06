# CourseSelect [![Build Status](https://travis-ci.org/PENGZhaoqing/CourseSelect.svg?branch=master)](https://travis-ci.org/PENGZhaoqing/CourseSelect)

### [中文教程1](http://blog.csdn.net/ppp8300885/article/details/52594839) [中文教程2](http://blog.csdn.net/ppp8300885/article/details/52601560) [中文教程3](http://blog.csdn.net/ppp8300885/article/details/52669749)


这个样本系统是基于国科大研究生课程 (高级软件工程) 开发的项目,目的是帮助入门者学习RoR (Ruby on Rails) 

适合新学者的入手的第一个项目 ([演示Demo戳这里](https://courseselect.herokuapp.com/ ))，入门者可以在这个样本系统上增加更多的功能:

* 处理选课冲突、控制选课人数
* 统计选课学分，学位课等
* 增加选课的开放、关闭功能
* 自定义管理员后台
* 基于OAuth的授权登陆
* Excel格式的数据导入
* 绑定用户邮箱（实现注册激活，忘记密码等）
* 站内查找检索 （课程按分类查找，过滤等）

### 目前功能：

* 多角色登陆（学生，老师，管理员）
* 学生动态选课，退课
* 老师动态增加，删除课程
* 老师对课程下的学生添加、修改成绩
* 权限控制：老师和学生只能看到自己相关课程信息

### 截图

<img src="/lib/screenshot1.png" width="700">  

<img src="/lib/screenshot2.png" width="700">

<img src="/lib/screenshot3.png" width="700">   

<img src="/lib/screenshot4.png" width="700">

## 说明

目前使用的库和数据库：

* 使用[Bootstrap](http://getbootstrap.com/)作为前端库
* 使用[Rails_admin Gem](https://github.com/sferik/rails_admin)作为后台管理
* 使用[Postgresql](http://postgresapp.com/)作为数据库

使用前需要安装Bundler，Gem，Ruby，Rails等依赖环境。

请根据本地系统下载安装[postgresql](https://devcenter.heroku.com/articles/heroku-postgresql#local-setup)数据库，并运行`psql -h localhost`检查安装情况。


## 安装

在终端（MacOS或Linux）中执行以下代码

```
$ git clone https://github.com/PENGZhaoqing/CourseSelect
$ cd CourseSelect
$ bundle install
$ sudo service postgresql start
$ rake db:create:all
$ rake db:migrate
$ rake db:seed
$ rails s -b $IP -p $PORT 
```
##往数据库中添加属性的命令：
1.
添加一个属性：
rails generate migration add_reset_to_users reset_digest:string
添加多个属性：
rails generate migration add_reset_to_users reset_digest:string reset_sent_at:datetime

2.bundle exec rake db:migrate:reset
（bundle exec rake db:migrate这个命令好像不对，用上面那个）

3.$ bundle exec rake db:seed

在浏览器中输入`localhost:3000`访问主页

##使用

1.学生登陆：

账号：`student1@test.com`

密码：`password`

2.老师登陆：

账号：`teacher1@test.com`

密码：`password`


3.管理员登陆：

账号：`admin@test.com`

密码：`password`

账号中数字都可以替换成2,3...等等


## Heroku云部署
##搭建Heroku环境
照着下面代码运行，应该就没问题

#为了准备好部署环境，下面要运行bundle install命令，并且指定一个特殊的选项，
#禁止在本地安装生成环境使用gem(即pg和rails_12factor)：
$ bundle install --without production
##提交改动：
$ git commit -a -m "Update Gemfile.lock for Heroku"
##检查系统中安装Heroku命令行客户端:(会看到版本号)
heroku create youappname
$ heroku version
##登陆Heroku账号，需要输入账号和密码
$ heroku login
##添加SSH密钥
$ heroku keys:add
##在Heroku上面部署你的应用，Heroku会为你的项目分配一个二级域名
 
##最后一步，把你的应用推送到Heroku
$ git push heroku master
 heroku rake db:migrate

项目可直接在Heroku上免费部署

1.fork此项目到自己Github账号下

2.创建Heroku账号以及Heroku app

3.将Heroku app与自己Github下的fork的项目进行连接

4.下载配置[Heroku CLI](https://devcenter.heroku.com/articles/heroku-command-line)命令行工具

5.运行`heroku login`在终端登陆，检查与heroku app的远程连接情况`git config --list | grep heroku`，若未检查到相应的app，请看[这里](http://stackoverflow.com/questions/5129598/how-to-link-a-folder-with-an-existing-heroku-app)

6.运行部署，详情[请戳这里](https://devcenter.heroku.com/articles/getting-started-with-rails4#rails-asset-pipeline)


## 测试

本项目包含了部分的测试（integration/fixture/model test），测试文件位于/test目录下。运行测试：

```
PENG-MacBook-Pro:IMS_sample PENG-mac$ rake test
Run options: --seed 15794

# Running:
.........

Finished in 1.202169s, 7.4865 runs/s, 16.6366 assertions/s.

9 runs, 20 assertions, 0 failures, 0 errors, 0 skips
```


## How to Contribute

先fork此项目，在分支修改后，pull request到主分支

提问请到issues里创建，欢迎contributor！

如果觉得好，给项目点颗星吧～


