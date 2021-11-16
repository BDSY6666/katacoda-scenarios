Enable Mysql Log and Log Housekeeping
1.create enable_log.cnf
`touch enable_log.cnf`{{execute}}

2.Create a folder db_data
`mkdir db_data`{{execute}}

3.Edit enable_log.cnf, add the following
[mysqld]
log_error = /var/lib/mysql/mysql_error.log

general_log_file = /var/lib/mysql/general.log
general_log = 1

slow_query_log=1
slow_query_log_file= /var/lib/mysql/slow.log
long_query_time=0.1

4.create a housekeep.sh file
`touch housekeep.sh`{{execute}}

5.add execute right
`chmod +x housekeep.sh`{{execute}}

6.edit the housekeep.sh file (PLEASE CHECK YOUR PATH FOR DB_DATA FOLDER)
nano housekeep.sh

path="/root/db_data/"

error_log_name="mysql_error.log"
general_log_name="general.log"
slow_logname="slow.log"
date=$(date '+%Y%m_%d')

#echo $path$error_log_name $path$error_logname$date

# housekeep error log
cat $path$error_log_name >> $path$error_log_name-$date
# housekeep general log
cat $path$general_log_name >> $path$general_log_name-$date
# housekeep slow log
cat $path$slow_log_name >> $path$slow_log_name-$date

7.Test the shell script
./housekeep.sh

8.Add script to cron job
crontab -e
59 11 * * *   /root/housekeep.sh

9.check error log
tail /root/db_data/mysql_error.log

10.check general log
tail /root/db_data/general.log

11.check slow log
tail /root/db_data/slow.log

12.check log housekeeped?
ls /root/db_data |grep 2021_11 



