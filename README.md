# 中国行政区划数据，省市区（县）镇村（乡）共五级
20160825 更新自 [http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2015/index.html](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2015/index.html "中国国家统计局2015")，共 **710740** 条数据

### 数据库为：MYSQL，表结构如下：
```sql
CREATE TABLE `rm_address_cnarea` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`area_code` CHAR(12) NOT NULL DEFAULT '' COMMENT '区域代码' COLLATE 'utf8_bin',
	`level` TINYINT(4) NOT NULL DEFAULT '0' COMMENT '层级，从0开始',
	`father` CHAR(12) NOT NULL DEFAULT '' COMMENT '父级区域代码' COLLATE 'utf8_bin',
	`name` VARCHAR(50) NOT NULL DEFAULT '' COMMENT '区域名称' COLLATE 'utf8_bin',
	`short_name` VARCHAR(50) NOT NULL DEFAULT '' COMMENT '简称' COLLATE 'utf8_bin',
	PRIMARY KEY (`id`),
	INDEX `father` (`father`)
)
COLLATE='utf8_bin'
ENGINE=MyISAM;
```

使用自取，如果有用，支持请访问：[bbmz.org](http://bbmz.org "斌斌妹子")

## 更新记录：
更新日期 | 条数 | 说明
----|------|----
| 20160824        | 707679           | 新建项目，初次更新  |
| 20160826        | 710740           | 调整更新脚本，再次更新  |
