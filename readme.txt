参考来自https://www.vinchin.com/en/blog/backup-synology-nas-to-wd-my-cloud.html这里有两种方式，

一种是synology通过自动任务进行同步到MyCloudEX2Ultra。
	将 My Cloud 挂载到 Synology
	1. 将 Synology 和 My Cloud 连接到路由器/交换机。
	2. 登录 DSM，打开File Station >工具>挂载远程文件夹> CIFS Shared Golder（适用于 SMB 共享）。需要输入WD的用户与密码。
	3. 输入 SMB 共享的路径（例如，\\10.0.1.40\NetBackup）和您的登录帐户详细信息。
	4. 选择安装位置并勾选“启动时自动安装”选项。单击安装。
	5. 在 File Station 中，就会有一个远程文件夹。
	6. 下面将参考这个网站内容https://post.smzdm.com/p/339940/
		设置同一个NAS下的目录文件夹同步。
	7. 打开控制面板-计划任务-新增-计划任务-用户自定义的脚本，粘贴进脚本，设置好执行时间，最好设置一下电子邮件通知，每天通知执行情况。
	8. 命令如下：rsync -avzhP --update 源目录地址（空格）目标目录地址
	rsync -avzhP --update /volume1/public /volume1/NetBackup  (注意：目标目录地址不需再加上目录名，只用 "源地址/目录名" to "目标目录地址")，执行后会在NetBackup下自动生成“public”目录

另一种是WD通过Rsync这个命令行程序，将synology的内容进行备份，区别就是用哪个NAS的CPU来烧脑。
