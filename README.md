# 中国行政区划数据，省市区（县）镇村（乡）共五级
## 使用说明
20180815 更新自 [2017年统计用区划代码和城乡划分代码(截止2017年10月31日)](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2017/index.html "中国国家统计局-2017年统计用区划代码和城乡划分代码")，共 **719474** 条数据

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
更新日期 | 条数 | 说明 | 数据源 |
----|------|----|----|
| 20160824        | 707679           | 新建项目，初次更新  |
| 20160826        | 710740           | 调整更新脚本，再次更新  |
| 20180106        | 712823           | 根据最新发布更新  | [2016年统计用区划代码和城乡划分代码](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2016/index.html "2016年统计用区划代码和城乡划分代码")
| 20180815        | 719474           | 根据2018-06-20发布更新   |[2017年统计用区划代码和城乡划分代码](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2017/index.html "2017年统计用区划代码和城乡划分代码")

## 附注
 > 本项目数据皆抓取自统计局网站，为避免对网站访问带来影响，只是用单线程采集，且每获取100次，sleep一分钟