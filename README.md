# LAB5
Database Replication
create user ‘rep02’@’%’ identified by ‘11223344’;
grant replication slave on *.* to ‘rep02’;
flush tables with read lock;
show master status;
unlock tables;

######################################################
stop slave;
change master to 
	 master_host=’192.168.1.2’,
	 master_user=’rep02’,
	 master_password=’11223344’,
	 master_log_file=’mysql-bin.000002’,
	 master_log_pos=1163072;
start slave;
