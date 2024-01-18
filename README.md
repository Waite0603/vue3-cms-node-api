> Fork 自 [https://github.com/waite0603/vue3-cms-node-api](https://github.com/waite0603/vue3-cms-node-api)

## 使用

1. 数据库导入 `mySql+api`, 修改 `db/index.js` 中的数据库配置
2. 安装依赖, 运行

```bash
npm install

node app.js
```
3. 如果需要修改端口, 可以在 `app.js` 中修改

## 问题

`Mysql 8.0+`报错如下 ER_NOT_SUPPORTED_AUTH_MODE: Client does not support authentication protocol requested by server; consider upgrading MySQL client

遇到的问题可能是由于MySQL 8.0及以上版本默认使用了新的密码验证插件“caching_sha2_password”，而旧的客户端可能不支持这个新的验证插件，所以会出现这个错误。

你可以通过修改MySQL的用户账户密码验证插件为“mysql_native_password”来解决这个问题。以下是在MySQL命令行中执行的命令：

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yourpassword';
FLUSH PRIVILEGES;
```

请将上述命令中的 'yourpassword' 替换为你的实际密码。

执行完上述命令后，你需要重新启动MySQL服务，然后再次尝试连接。