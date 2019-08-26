# English-Chinese-dictionary(with phonetic symbols)
Import the CSV format of the English-Chinese dictionary into MySQL

### Create tables:

```
CREATE TABLE `tb_words_dict` (

  `id` int(11) NOT NULL AUTO_INCREMENT,

  `word` varchar(164) COLLATE utf8_bin NOT NULL,

  `sw` varchar(64) COLLATE utf8_bin NOT NULL,

  `phonetic` varchar(64) COLLATE utf8_bin DEFAULT NULL,

  `definition` text COLLATE utf8_bin,

  `translation` text COLLATE utf8_bin,

  `pos` varchar(16) COLLATE utf8_bin DEFAULT NULL,

  `collins` varchar(11) COLLATE utf8_bin DEFAULT '0',

  `oxford` varchar(11) COLLATE utf8_bin DEFAULT '0',

  `tag` varchar(64) COLLATE utf8_bin DEFAULT NULL,

  `bnc` varchar(11) COLLATE utf8_bin DEFAULT NULL,

  `frq` varchar(11) COLLATE utf8_bin DEFAULT NULL,

  `exchange` text COLLATE utf8_bin,

  `detail` text COLLATE utf8_bin,

  `audio` text COLLATE utf8_bin,

  PRIMARY KEY (`id`),

  UNIQUE KEY `唯一word` (`word`) USING BTREE,

  UNIQUE KEY `id` (`id`) USING BTREE

) ENGINE=InnoDB AUTO_INCREMENT=8359808 DEFAULT CHARSET=utf8 COLLATE=utf8_bin

```

### Import database:

```
load data infile '/private/tmp/words_dict.csv' 

replace into table tb_words_dict 

fields terminated by ',' 

optionally enclosed by '"' 

lines terminated by '\n' 

ignore 1 lines(word,phonetic,definition,translation,pos,collins,oxford,tag,bnc,frq,exchange,detail,audio);

```
