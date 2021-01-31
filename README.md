# MySQL

CREATE DATABASE elvis_stores;

USE elvis_stores;

CREATE TABLE email_list(first_name VARCHAR(20),last_name VARCHAR(20),email VARCHAR(60));

DESCRIBE email_list;//显示表结构

DROP TABLE email_list;//删除表

INSERT INTO email_list(first_name,last_name,email) VALUES('$first_name','$last_name','$email');

SELECT * FROM email_list WHERE first_name='lin';

DELETE FROM email_list WHERE first_name='lin';

ALTER TABLE guitarwards ADD COLUMN approved TINYINT;//加列

ALTER TABLE guitarwards ADD COLUMN approved ENUM('yes','no');//枚举

ALTER TABLE guitarwards MODIFY COLUMN approved TINYINT DEFAULT 0;//修改列

ALTER TABLE mismatch_users ADD username VARCHER(32) NO NULL AFTER user_id,ADD password VARCHAR(16) NOT NULL AFTER username;//特定某列后面添加列

ALTER TABLE mismatch_users CHANGE password password VARCHER(40) NOT NULL;

//多个表的查询

SELECT mismatch_topic.topic_id,mismatch_category.name FROM mismatch_topic INNER JOIN mismatch_category ON(miscatch_topic.category_id==mismatch_category.category_id);

//多个表别名

SELECT mr.response_id,mr.topic_id,mr.response,mt.name AS topic_name,mc.name AS category_name FROM mismatch_response AS mr INNER JOIN mismatch_topic AS mt USING (topic_id) INNER JOIN mismatch_category AS mc USING (category_id) WHERE mr.user_id='. $_SESSION['user_id']';