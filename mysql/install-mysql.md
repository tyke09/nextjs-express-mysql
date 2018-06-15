# 准备mysql数据库

​	

## 介绍

本文描述mysql的安装步骤。开发环境如下：

win10 x64

​	

## 下载

下载地址如下：

```shell
# 官网
https://www.mysql.com/

# win10 x64可用的下载链接
https://dev.mysql.com/get/Downloads/MySQLInstaller/mysql-installer-community-8.0.11.0.msi

# workbench下载链接
https://dev.mysql.com/get/Downloads/MySQLGUITools/mysql-workbench-community-6.3.10-winx64.msi
```

​	

## 安装和配置mysql

运行下载下来的文件 `mysql-installer-community-8.0.11.0.msi`；

在 `License Agreement` 步骤勾选 `I accept the license terms` ，点 `Next > `；

在 `Choosing a Setup Type` 步骤选择 `Developer Default` ，且选择 `Install all products` ，点 `Next >` ；

在 `Check Requirements` 步骤中，提示 `Python 2.7(32-bit) is not installed` ，不管它，直接点 `Next > ` ；

在 `Installation` 步骤中，列出了即将安装的产品列表，直接点 `Execute` ；

全部安装完成后，点击 `Next >` ；

在 `Product Configuration` 步骤中，直接点击 `Next > ` ；

在 `Group Replication` 步骤中，使用默认选项，直接点击 `Next > ` ；

在 `Type and Networking` 步骤中，使用默认选项，直接点击 `Next > ` ；

在 `Authentication Method` 步骤中，使用默认选项，直接点击 `Next > ` ；

在 `Accounts and Roles` 步骤中，填写root密码，填写后点击 `Next >` ;

在 `Windows Service` 步骤中，使用默认选项，直接点击 `Next >` ;

在 `Plugins and Extensions` 步骤中，使用默认选项，直接点击 `Next >` ;

在 `Apply Configuration` 步骤中，直接点击 `Execute` ；

完成后，点击 `Finish` ；

回到 `Product Configuration` 步骤，点击 `Next > ` ；

进入 `MySQL Router Configuration` ，直接点击 `Finish` ；

回到 `Product Configuration` 步骤，点击 `Next > ` ；

进入 `Connect To Server` 步骤，输入刚才配置的root密码，点击 `Check` ，提示测试通过。点击 `Next >` ;

在 `Apply Configuration` 步骤中，直接点击 `Execute` ；

完成后，点击 `Finish` ；

回到 `Product Configuration` 步骤，点击 `Next > ` ；

进入 `Installation Complete` 步骤，取消两个打勾，点击 `Finish` 。	