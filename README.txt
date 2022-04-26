###################################	PHP	###################################	
Per il servizio php servirà una cartella mio-sito che conterrà i file che utilizzati all'accesso dell'URL "http://localhost:8080"
Per avviare il servizio PHP:

docker run -d -p 8080:80 --name my-apache-php-app --rm  -v /home/somepath/mio-sito:/var/www/html zener79/php:7.4-apache

###################################	MySQL	###################################	
Per il servizio del database di mysql bisogna creare una cartella dump, la cartella dovrà contenere un file per la creazione del database, il nome del file è create_employee.sql
Per avviare il servizio del datbase mysql utilizzare questi comandi:

docker run --name my-mysql-server --rm -v /home/somepath/mysqldata:/var/lib/mysql -v /home/somepath/dump:/dump -e MYSQL_ROOT_PASSWORD=my-secret-pw -p 3306:3306 -d mysql:latest
docker exec -it my-mysql-server bash
mysql -u root -p < /dump/create_employee.sql; exit;

--------------------------------------->NOTA: modificare il path dei comandi

Per entrare nell'immagine di MySQL: 
	docker exec -it my-mysql-server bash

Per poter utilizzare il database con SQL: 
	mysql -u root -p
	password: my-secret-pw