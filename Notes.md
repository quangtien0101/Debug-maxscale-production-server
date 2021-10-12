## Maxscale log
```
2021-10-12 08:25:02.634   notice : (set_version): 'omniagent_db01_16_191' sent version string '10.5.12-MariaDB-log'. Detected type: 'MariaDB', version: 10.5.12.
2021-10-12 08:25:02.638   notice : (mxs_update_server_charset): Server 'omniagent_db01_16_191' charset: latin1
2021-10-12 08:25:02.643   notice : (set_version): 'omniagent_db01_16_192' sent version string '10.5.12-MariaDB-log'. Detected type: 'MariaDB', version: 10.5.12.
2021-10-12 08:25:02.647   notice : (mxs_update_server_charset): Server 'omniagent_db01_16_192' charset: latin1
2021-10-12 08:25:02.652   notice : (set_version): 'omniagent_db01_16_193' sent version string '10.5.12-MariaDB-log'. Detected type: 'MariaDB', version: 10.5.12.
2021-10-12 08:25:02.658   notice : (mxs_update_server_charset): Server 'omniagent_db01_16_193' charset: latin1
2021-10-12 08:25:02.690   notice : (service_launch_all): Starting a total of 1 services...
2021-10-12 08:25:02.691   notice : (production_galera_cluster_listener); (listen): Listening for connections at [::]:6008
2021-10-12 08:25:02.691   notice : (service_launch_all): Service 'production_galera_cluster_service' started (1/1)
2021-10-12 08:25:02.700   warning: (load_users_mariadb): Using old user account query due to insufficient privileges. To avoid this warning, give the service user of 'production_galera_cluster_service' access to the 'mysql.procs_priv'-table.
2021-10-12 08:25:02.706   notice : (update_users): Read 11 user@host entries from 'omniagent_db01_16_193' for service 'production_galera_cluster_service'.
2021-10-12 08:25:05.360   warning: (102) (get_route_target): The query can't be routed to all backend servers because it includes SELECT and SQL variable modifications which is not supported. Set use_sql_variables_in=master or split the query to two, where SQL variable m
odifications are done in the first and the SELECT in the second one.
2021-10-12 08:25:05.371   warning: (102) (get_route_target): The query can't be routed to all backend servers because it includes SELECT and SQL variable modifications which is not supported. Set use_sql_variables_in=master or split the query to two, where SQL variable m
odifications are done in the first and the SELECT in the second one.
2021-10-12 08:25:05.389   warning: (102) (get_route_target): The query can't be routed to all backend servers because it includes SELECT and SQL variable modifications which is not supported. Set use_sql_variables_in=master or split the query to two, where SQL variable m
odifications are done in the first and the SELECT in the second one.
2021-10-12 08:25:05.406   warning: (102) (get_route_target): The query can't be routed to all backend servers because it includes SELECT and SQL variable modifications which is not supported. Set use_sql_variables_in=master or split the query to two, where SQL variable m
odifications are done in the first and the SELECT in the second one.
2021-10-12 08:25:05.424   warning: (102) (get_route_target): The query can't be routed to all backend servers because it includes SELECT and SQL variable modifications which is not supported. Set use_sql_variables_in=master or split the query to two, where SQL variable m
odifications are done in the first and the SELECT in the second one.
2021-10-12 08:25:13.581   warning: (446) (get_route_target): The query can't be routed to all backend servers because it includes SELECT and SQL variable modifications which is not supported. Set use_sql_variables_in=master or split the query to two, where SQL variable m
odifications are done in the first and the SELECT in the second one.
2021-10-12 08:25:24.530   error  : (800) (track_query): debug assert at /home/timofey_turenko_mariadb_com/MaxScale/server/modules/protocol/MariaDB/mariadb_backend.cc:2360 failed: m_state == State::ROUTING || m_state == State::SEND_HISTORY || m_state == State::READ_HISTOR
Y || m_state == State::PREPARE_PS || m_state == State::SEND_CHANGE_USER
debug assert at /home/timofey_turenko_mariadb_com/MaxScale/server/modules/protocol/MariaDB/mariadb_backend.cc:2360 failed: m_state == State::ROUTING || m_state == State::SEND_HISTORY || m_state == State::READ_HISTORY || m_state == State::PREPARE_PS || m_state == State::S
END_CHANGE_USER
alert  : MaxScale 6.1.2 received fatal signal 6. Commit ID: 1479685b53546a0758137c81b864539a80b13bbc System name: Linux Release string: CentOS Linux release 7.9.2009 (Core)

```


```
warning: (load_users_mariadb): Using old user account query due to insufficient privileges. To avoid this warning, give the service user of 'production_galera_cluster_service' access to the 'mysql.procs_priv'-table.
notice : (update_users): Read 11 user@host entries from 'omniagent_db01_16_193' for service 'production_galera_cluster_service'.
warning: (102) (get_route_target): The query can't be routed to all backend servers because it includes SELECT and SQL variable modifications which is not supported. Set use_sql_variables_in=master or split the query to two, where SQL variable m
odifications are done in the first and the SELECT in the second one.
```

## Query log
```
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,use `omniagent_db`;
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,set names 'utf8' collate 'utf8_unicode_ci'
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,set session sql_mode='NO_ENGINE_SUBSTITUTION'
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,select count(*) as aggregate from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,select *,sum(total_call_per_day) as total_call, sum(httt) as s_total_httt,sum(htkt) as s_total_htkt from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? 
and ? and `total_call_per_day` > ? group by `user_id` order by `user_history_log_date` desc limit 15 offset 0
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,select count(*) as aggregate from `kb_user_history_hubchat_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,select * from information_schema.tables where table_schema = ? and table_name = ?
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,select `kb_history_202110`.`history_cuser` as `user_name`, `kb_history_202110`.`history_user_id` as `user_id`, SUM(IF(history_group = 1,1,0)) as httt, SUM(IF(history_group = 2,1,0)) as 
htkt, COUNT(history_id) as total_call from `kb_history_202110` inner join `kb_uber` on `kb_history_202110`.`history_id` = `kb_uber`.`historyID` where `history_user_id` = ? and `kb_history_202110`.`history_deleted` = ? and `kb_history_202110`.`history_temp` = ? and `kb_hi
story_202110`.`history_status` > ? and `kb_history_202110`.`history_fail_info` = ? and `kb_uber`.`isProcess` = ? and `kb_history_202110`.`history_start_call` between ? and ? group by `kb_history_202110`.`history_user_id` order by `kb_history_202110`.`history_cuser` asc
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,select * from information_schema.tables where table_schema = ? and table_name = ?
production_galera_cluster_service,5,2021-10-12 08:48:35,omniagent@::ffff: ,select `history_cuser`, SUM(IF(history_uber_id IS NOT NULL, 1, 0)) AS total_support,                                                          SUM(IF(history_content LIKE '23327;23328%',
 1, 0)) AS total_not_support from `kb_history_202110` where `history_cuser` = ? and `history_fail_info` in (?, ?, ?) and `history_deleted` = ? and `history_temp` = ? and `history_status` <> ? and `history_start_call` between ? and ? group by `history_cuser`
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,use `omniagent_db`;
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,set names 'utf8' collate 'utf8_unicode_ci'
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,set session sql_mode='NO_ENGINE_SUBSTITUTION'
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,select count(*) as aggregate from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,select *,sum(total_call_per_day) as total_call, sum(httt) as s_total_httt,sum(htkt) as s_total_htkt from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id` order by `user_history_log_date` desc limit 15 offset 0                                                                                                                                                                  
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,select count(*) as aggregate from `kb_user_history_hubchat_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`          
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,select * from information_schema.tables where table_schema = ? and table_name = ?                                                                                                        
production_galera_cluster_service,6,2021-10-12 08:48:35,omniagent@::ffff: ,select `kb_history_202110`.`history_cuser` as `user_name`, `kb_history_202110`.`history_user_id` as `user_id`, SUM(IF(history_group = 1,1,0)) as httt, SUM(IF(history_group = 2,1,0)) as htkt, COUNT(history_id) as total_call from `kb_history_202110` inner join `kb_uber` on `kb_history_202110`.`history_id` = `kb_uber`.`historyID` where `history_user_id` = ? and `kb_history_202110`.`history_deleted` = ? and `kb_history_202110`.`history_temp` = ? and `kb_history_202110`.`history_status` > ? and `kb_history_202110`.`history_fail_info` = ? and `kb_uber`.`isProcess` = ? and `kb_history_202110`.`history_start_call` between ? and ? group by `kb_history_202110`.`history_user_id` order by `kb_history_202110`.`history_cuser` asc  
production_galera_cluster_service,5,2021-10-12 08:48:36,omniagent@::ffff: ,select `user_id`, `user_name`, `user_level`, `user_level_group`, `user_password`, `user_fullname`, `user_email`, `user_phone`, `user_group_id`, `user_joindate`, `user_location`, `user_lastaction`, `user_number`, `user_lastvisit`, `user_dept_id`, `user_postion_id`, `user_ip_phone`, `user_com_level`, `user_contract`, `user_group_agent_id`, `user_group_agent_id_main`, `user_resource`, `user_region`, `user_httd`, `user_country`, `user_firstlogin`, `process_status`, `lastactive`, `type_login`, `date_login`, `user_avatar`, `user_birthday`, `staff_id`, `user_avatar_circle` from `kb_users` where `user_email` = ? limit 1                                                                                                            
production_galera_cluster_service,5,2021-10-12 08:48:36,omniagent@::ffff: ,select * from `kb_caseable` where `kb_caseable`.`process_status` = ? order by `ca_priority` asc                                                                                          
production_galera_cluster_service,6,2021-10-12 08:48:36,omniagent@::ffff: ,select * from information_schema.tables where table_schema = ? and table_name = ?                                                                                                        
production_galera_cluster_service,5,2021-10-12 08:48:36,omniagent@::ffff: ,select `call_id`, `call_desk`, `call_phone`, `call_start_call`, `call_customer_phone`, `call_status`, `call_ip`, `call_transfer`, `call_IDinside`, `call_CCallerID` from `kb_call` where `call_status` = ? and `call_ip` = ? and (UNIX_TIMESTAMP() - 2700) < call_start_call and `call_IDinside` <> ? and `call_CCallerID` <> ? order by `call_id` desc limit 1                                                                                                         
production_galera_cluster_service,6,2021-10-12 08:48:36,omniagent@::ffff: ,select `history_cuser`, SUM(IF(history_uber_id IS NOT NULL, 1, 0)) AS total_support,                                                          SUM(IF(history_content LIKE '23327;23328%', 1, 0)) AS total_not_support from `kb_history_202110` where `history_cuser` = ? and `history_fail_info` in (?, ?, ?) and `history_deleted` = ? and `history_temp` = ? and `history_status` <> ? and `history_start_call` between ? and ? group by `history_cuser`              
production_galera_cluster_service,5,2021-10-12 08:48:36,omniagent@::ffff: ,select `history_session_id`, `history_id` from `kb_history` where `history_id_call` = ? order by `history_id` desc limit 1 
```

```
use `omniagent_db`;
set names 'utf8' collate 'utf8_unicode_ci'
set session sql_mode='NO_ENGINE_SUBSTITUTION'
select count(*) as aggregate from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`
select *,sum(total_call_per_day) as total_call, sum(httt) as s_total_httt,sum(htkt) as s_total_htkt from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? 
select count(*) as aggregate from `kb_user_history_hubchat_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`
select * from information_schema.tables where table_schema = ? and table_name = ?
select `kb_history_202110`.`history_cuser` as `user_name`, `kb_history_202110`.`history_user_id` as `user_id`, SUM(IF(history_group = 1,1,0)) as httt, SUM(IF(history_group = 2,1,0)) as 
select * from information_schema.tables where table_schema = ? and table_name = ?
select `history_cuser`, SUM(IF(history_uber_id IS NOT NULL, 1, 0)) AS total_support,                                                          SUM(IF(history_content LIKE '23327;23328%',
use `omniagent_db`;
set names 'utf8' collate 'utf8_unicode_ci'
set session sql_mode='NO_ENGINE_SUBSTITUTION'
select count(*) as aggregate from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`
select *,sum(total_call_per_day) as total_call, sum(httt) as s_total_httt,sum(htkt) as s_total_htkt from `kb_user_history_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id` order by `user_history_log_date` desc limit 15 offset 0                                                                                                                                                                  
select count(*) as aggregate from `kb_user_history_hubchat_log` where `user_id` = ? and `user_history_log_date` between ? and ? and `total_call_per_day` > ? group by `user_id`          
select * from information_schema.tables where table_schema = ? and table_name = ?                                                                                                        
select `kb_history_202110`.`history_cuser` as `user_name`, `kb_history_202110`.`history_user_id` as `user_id`, SUM(IF(history_group = 1,1,0)) as httt, SUM(IF(history_group = 2,1,0)) as htkt, COUNT(history_id) as total_call from `kb_history_202110` inner join `kb_uber` on `kb_history_202110`.`history_id` = `kb_uber`.`historyID` where `history_user_id` = ? and `kb_history_202110`.`history_deleted` = ? and `kb_history_202110`.`history_temp` = ? and `kb_history_202110`.`history_status` > ? and `kb_history_202110`.`history_fail_info` = ? and `kb_uber`.`isProcess` = ? and `kb_history_202110`.`history_start_call` between ? and ? group by `kb_history_202110`.`history_user_id` order by `kb_history_202110`.`history_cuser` asc  
select `user_id`, `user_name`, `user_level`, `user_level_group`, `user_password`, `user_fullname`, `user_email`, `user_phone`, `user_group_id`, `user_joindate`, `user_location`, `user_lastaction`, `user_number`, `user_lastvisit`, `user_dept_id`, `user_postion_id`, `user_ip_phone`, `user_com_level`, `user_contract`, `user_group_agent_id`, `user_group_agent_id_main`, `user_resource`, `user_region`, `user_httd`, `user_country`, `user_firstlogin`, `process_status`, `lastactive`, `type_login`, `date_login`, `user_avatar`, `user_birthday`, `staff_id`, `user_avatar_circle` from `kb_users` where `user_email` = ? limit 1                                                                                                            
select * from `kb_caseable` where `kb_caseable`.`process_status` = ? order by `ca_priority` asc                                                                                          
select * from information_schema.tables where table_schema = ? and table_name = ?                                                                                                        
select `call_id`, `call_desk`, `call_phone`, `call_start_call`, `call_customer_phone`, `call_status`, `call_ip`, `call_transfer`, `call_IDinside`, `call_CCallerID` from `kb_call` where `call_status` = ? and `call_ip` = ? and (UNIX_TIMESTAMP() - 2700) < call_start_call and `call_IDinside` <> ? and `call_CCallerID` <> ? order by `call_id` desc limit 1                                                                                                         
select `history_cuser`, SUM(IF(history_uber_id IS NOT NULL, 1, 0)) AS total_support,                                                          SUM(IF(history_content LIKE '23327;23328%', 1, 0)) AS total_not_support from `kb_history_202110` where `history_cuser` = ? and `history_fail_info` in (?, ?, ?) and `history_deleted` = ? and `history_temp` = ? and `history_status` <> ? and `history_start_call` between ? and ? group by `history_cuser`              
select `history_session_id`, `history_id` from `kb_history` where `history_id_call` = ? order by `history_id` desc limit 1
```
## Identify problem
The query that caused warnings --> crash
```sql
SELECT T2.case_id, T2.case_title FROM 
( SELECT @r AS _id, (SELECT @r := case_parent FROM kb_cases WHERE case_id = _id) AS case_parent, @l := @l + 1 AS lvl FROM (SELECT @r := 18867, @l := 0) vars, kb_cases h WHERE @r <> 0) T1 JOIN kb_cases T2 ON T1._id = T2.case_id WHERE T2.process_status = 'publish' ORDER BY T1.lvl DESC;
```

Create a test database, table with a column has an integer type
```sql
CREAT DATABASE test;
USE test;
CREATE TABLE t1(id INT);
```

Insert some dummy data
```sql
INSERT INTO test.t1 (id) VALUES (0);
INSERT INTO test.t1 (id) VALUES (1);
INSERT INTO test.t1 (id) VALUES (2);
```

Test query to regenerate the error
```sql
#test query
set @id=1;
SELECT @id := @id + 1 FROM test.t1;
```

Clean up
```sql
DROP DATABASE test
```
