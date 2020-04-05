#### cron
* 在某个预设的时间执行的脚本，cron程序会在后台运行并检查特殊的cron时间表来获得计划执行得脚本
* crontab命令来处理cron时间表
* 会检查语法是否正确
* crontab -e
* cron在/var/spool/cron目录下找到文件后，将找到的文件加载到内存
* 
* /etc/crontab是一个文件，只有root才能修改
* cron时间表
* minutes hour ++day of month++  month ++day of week++
* 0-59 0-23 1-31 1-12 0-6 0表示周日
* 每个字段可能包含星号*，表示first-last
* 允许1，2，6  或0-4，8-12
* 步长值  /<number>  0-23/2表示零点到二十三点，每隔两小时执行一次
* 第六字段指要运行的部分，直到换行或%
* 要注意百分号
* 满足一个条件就会执行，天数与星期几
* 要应用整个系统，/etc/crontab
* crontab 只能实现分钟级别,要秒级使用modtime和inotify
* 适合周期性的日志分析和数据备份的作业
* /etc/cron.deny 或/etc/cron.allow
* crontab [-u user] file crontab [-u user] [-e -l -r]
* -e编辑某个用户的crontab文件
* -l 列出
* -r 删除
* crontab -l >crontab.backup 备份
