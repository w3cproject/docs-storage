## Restore dump with .backup extension (or other)

`psql -h localhost -p 5433 -d dbName -U UserName -f pathToBackUp.backup`

or

`psql -h localhost -p 5433 -U user -d db_name < /directory/archive.sql`

[Source stackoverflow](https://stackoverflow.com/questions/2732474/restore-a-postgres-backup-file-using-the-command-line)

## Create backup

`pg_dump -h localhost -p 5432 -U user -d db_name > backup_name.sql`

[Source stackoverflow](https://stackoverflow.com/questions/2732474/restore-a-postgres-backup-file-using-the-command-line)