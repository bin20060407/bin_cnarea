# 中国行政区划数据，省市区（县）镇村（乡）共五级
## 使用说明
20190314 更新自 [2018年统计用区划代码和城乡划分代码(截止2018年10月31日)](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2018/index.html "2018年统计用区划代码和城乡划分代码(截止2018年10月31日")，共 **712182** 条数据

### 数据库为：MYSQL，表结构如下：
```sql
CREATE TABLE `bin_cnarea` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`area_code` CHAR(12) NOT NULL DEFAULT '' COMMENT '区域代码' COLLATE 'utf8_bin',
	`level` TINYINT(4) NOT NULL DEFAULT '0' COMMENT '层级，从0开始',
	`father` CHAR(12) NOT NULL DEFAULT '' COMMENT '父级区域代码' COLLATE 'utf8_bin',
	`name` VARCHAR(50) NOT NULL DEFAULT '' COMMENT '区域名称' COLLATE 'utf8_bin',
	`short_name` VARCHAR(50) NOT NULL DEFAULT '' COMMENT '简称' COLLATE 'utf8_bin',
	PRIMARY KEY (`id`),
	UNIQUE INDEX `area_code` (`area_code`),
	INDEX `father` (`father`)
)
COMMENT='Binbin 中国行政区域表'
COLLATE='utf8_bin'
ENGINE=InnoDB
;
```

使用自取，如果有用，请点击Star

## 更新记录：

|更新日期 | 条数 | 说明 | 数据源 |
| ---- | ------ | ---- | ---- |
| 20160824        | 707679           | 新建项目，初次更新  |
| 20160826        | 710740           | 调整更新脚本，再次更新  |
| 20180106        | 712823           | 根据最新发布更新  | [2016年统计用区划代码和城乡划分代码](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2016/index.html "2016年统计用区划代码和城乡划分代码") |
| 20180815        | 719474           | 根据2018-06-20发布更新   | [2017年统计用区划代码和城乡划分代码](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2017/index.html "2017年统计用区划代码和城乡划分代码") |
| 20190314        | 712182           | 根据最新发布更新  | [2018年统计用区划代码和城乡划分代码(截止2018年10月31日)](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2018/index.html "2018年统计用区划代码和城乡划分代码(截止2018年10月31日") |

---
### 20190314 更新
- 采用全新脚本获取数据，所有 `URL` 全部入库，共计：46829
- 由一个脚本分解成 `城市`、`县`，`镇`、`村`分开处理
- 使用队列来保证任务可靠性，也方便失败后进行重试

## Todo
- [ ] 提供在线 demo，方便查看数据

## 附注
 > 本项目数据皆抓取自统计局网站，为避免对网站访问带来影响，只是用单线程采集，且每获取100次，sleep一分钟