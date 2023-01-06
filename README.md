# docker-compose-mysql-wordpress.yaml
docker network create wordpress:
docker container run --name mysql-container --rm --network wordpress -e MYSQL_ROOT_PASSWORD=wordpress -d mysql:5.7
docker container run --name wordpress-container --rm --network wordpress -e WORDPRESS_DB_HOST=mysql-container -e WORDPRESS_DB_PASSWORD=wordpress -p 8090:80 -d wordpress
