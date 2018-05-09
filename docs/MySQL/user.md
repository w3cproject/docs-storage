## Create user with password

```mysql
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```

## Grant privileges

```mysql
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
```

## Check privileges

```mysql
FLUSH PRIVILEGES;
```

## Delete user

```mysql
DROP USER ‘demo’@‘localhost’;
```

## List of privileges and description

- `ALL PRIVILEGES` - как мы видели ранее, это даст пользователю MySQL полный доступ к заданной базе данных (если база данных не указана, то ко всем).
- `CREATE` - позволяет создавать новые таблицы или базы данных.
- `DROP` - позволяет удалять таблицы или базы данных.
- `DELETE` - позволяет удалять строки из таблиц.
- `INSERT` - позволяет добавлять строки в таблицу.
- `SELECT` - поволит использовать команду Select для чтения из баз данных.
- `UPDATE` - позволит редактировать строки таблиц.
- `GRANT OPTION` - позволит назначать или удалять права доступа для других пользователей.

## Add privileges

```mysql
GRANT [тип прав] ON [название базы данных].[название таблицы] TO ‘[имя пользователя]’@'localhost’;
```

## Remove privileges

```mysql
REVOKE [тип прав] ON [название базы данных].[название таблицы] FROM ‘[имя пользователя]’@‘localhost’;
```