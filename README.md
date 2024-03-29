# auto-investor-db

https://docs.liquibase.com/tools-integrations/maven/workflows/creating-liquibase-projects-with-maven-postgresql.html

https://blog.knoldus.com/liquibase-with-maven-and-postgresql/

Running liquibase from command line:
	mvn liquibase:update
	mvn liquibase:rollback -Dliquibase.rollbackCount=2

	mvn liquibase:update -DpropertiesFile=sim.liquibase.properties
	mvn liquibase:rollback -DpropertiesFile=sim.liquibase.properties -Dliquibase.rollbackCount=2
	
Postgres:
	https://www.baeldung.com/ops/postgresql-docker-setup
	
	docker stop 5eaf702264eb
	docker container ls
	docker pull postgres:16.0
	docker rm postgresql
	
	docker run -itd -e POSTGRES_USER=sa -e POSTGRES_PASSWORD=password -p 5432:5432 -v C:\Users\trent\eclipse-workspace\auto-investor-db-data:/var/lib/postgresql/data --name postgresql postgres:16.0
	docker run -itd -e POSTGRES_USER=sa -e POSTGRES_PASSWORD=password -p 5433:5432 -v C:\Users\trent\eclipse-workspace\auto-investor-simulator-db-data:/var/lib/postgresql/data --name postgresql-simulator postgres:16.0
	
	jdbc:postgresql://localhost:5432/sa
	


sql:
	see query planner in Squirrel
		EXPLAIN SELECT * FROM OPTION_CHAINS WHERE SYMBOL = 'SPY' AND EXPIRATION = '2023-12-31' AND VALUATION_DATE = '2023-11-27';

	SELECT pg_sequence_last_value('public.option_types_id_seq'); -- last value of sequence
	select * from stocks;	
	
list schemas:
	SELECT schema_name
	FROM information_schema.schemata;
	
postgresql: for a given table name what is schema name? - https://stackoverflow.com/questions/30621921/postgresql-for-a-given-table-name-what-is-schema-name
	SELECT table_catalog, table_schema 
	FROM   information_schema.tables 
	WHERE  table_name = 'student'
	
How to get the name of the current database from within PostgreSQL? - https://dba.stackexchange.com/questions/58312/how-to-get-the-name-of-the-current-database-from-within-postgresql
	SELECT current_database();
	