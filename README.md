<img src="https://github.com/chdb-io/chdb/raw/main/docs/_static/snake-chdb.png" width=300>

[![PyPI](https://img.shields.io/pypi/v/chdb.svg)](https://pypi.org/project/chdb/)
[![Downloads](https://static.pepy.tech/badge/chdb)](https://pepy.tech/project/chdb)
[![Discord](https://img.shields.io/discord/1098133460310294528?logo=Discord)](https://discord.gg/Njw5YXSPPc)

# chDB-CLI
Simple CLI / REPL for [chdb](https://chdb.io) made in Python

#### Setup
```bash
wget https://raw.githubusercontent.com/chdb-io/chdb-cli/main/chdb-cli.py -O chdb-cli
chmod +x chdb-cli
```
#### Usage
By default, chDB-cli will create a temporary, self-cleaning database folder for your data.<br>
To open or create a persistent database, simply include a database folder path as a command line argument.

##### Temporary DB Folder
```
./chdb-cli
```

```sql

Connected to auto-clean temporary database.
CTRL-D to Exit. ESC+ENTER or ; to Run.
CHDB VERSION: 0.11.5

:) SELECT 'hello chdb', version() as version;
┏━━━━━━━━━━━━━━┳━━━━━━━━━━┓
┃ 'hello chdb' ┃ version  ┃
┡━━━━━━━━━━━━━━╇━━━━━━━━━━┩
│ hello chdb   │ 23.6.1.1 │
└──────────────┴──────────┘
```

##### Custom DB Folder
```
./chdb-cli /tmp/chdb
```
```sql
Connected to local database /tmp/chdb
CTRL-D to Exit. ESC+ENTER or ; to Run.
CHDB VERSION: 0.11.5

:) CREATE DATABASE IF NOT EXISTS db_xxx ENGINE = Atomic;

:) CREATE TABLE IF NOT EXISTS db_xxx.log_table_xxx (x String, y Int) ENGINE = Log;

:) INSERT INTO db_xxx.log_table_xxx VALUES ('a', 1), ('b', 3), ('c', 2), ('d', 5);

:) CREATE VIEW db_xxx.view_xxx AS SELECT * FROM db_xxx.log_table_xxx LIMIT 4;

:) SELECT * FROM db_xxx.view_xxx;

┏━━━┳━━━┓
┃ x ┃ y ┃
┡━━━╇━━━┩
│ a │ 1 │
├───┼───┤
│ b │ 3 │
├───┼───┤
│ c │ 2 │
├───┼───┤
│ d │ 5 │
└───┴───┘
```

#### CLI Screenshot

![image](https://github.com/chdb-io/chdb-cli/assets/1423657/97a4fca0-ad8c-4c67-bc33-6f406656adb3)
