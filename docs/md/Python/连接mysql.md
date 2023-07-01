<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-17 16:12:00
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-17 16:30:43
 * @FilePath: \knowledge_planet\docs\md\Python\连接mysql.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

> ### 引入第三方包

```linux
pip install pymysql
```

> ### 配置数据库连接信息

```python
import pymysql

db_config_info = {
    'host': "XXXXX",
    'username': 'XXXX',
    'password': 'XXXX',
    'database': 'XXXX',
    'port': 3306
}

mysqldb = pymysql.connection(
    host=db_config_info['host'],
    user=db_config_info['username'],
    password=db_config_info['password'],
    db=db_config_info['database'],
    port= db_config_info['port'],
    charset='utf-8'
)


# 查询
def query(sql):
    # 获得游标对象
    cursor = mysqldb.cursor(cursor=pymysql.cursors.DictCursor)
    # 执行sql语句
    cursor.execute(sql)
    result = cursor.fetchall()
    mysqldb.commit()
    mysqldb.close()
    return result

# 查询
def find_data_by_id(table, ids):
    sql = f'select * from `{table}` where id = `{ids}`'
    return query(sql)

# 更新
def update_data_by_id(table, values, ids):
    sql = f'UPDATE `{table}` SET `{values}` WHERE id = `{ids}`'
    return query(sql)

# 删除
def delete_data(table, ids):
    sql = f'DELETE FROM `{table}` WHERE id = `{ids}`'
    return query(sql)

# 添加
def add_data(table, values):
    sql = f'INSERT INTO `{table}` SET `{values}`'
    return query(sql)

```
