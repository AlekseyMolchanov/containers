sql_pull:
	docker pull mcr.microsoft.com/mssql/server:2017-latest

sql_run:
	docker run --rm -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=pass' -d  -p 1433:1433 --name dpa_sql mcr.microsoft.com/mssql/server:2017-latest

sql_change_pass:
	docker exec -it dpa_sql /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'old_pass' -Q 'ALTER LOGIN SA WITH PASSWORD="new_dpa"'

build:
	docker build -t dpa .

run:
	docker run --rm -i -t -d -p 8123:8123 -p 8124:8124 --name dpa dpa

stop:
	docker ps -q --filter "name=dpa" | grep -q . && docker stop dpa || echo Not Found



