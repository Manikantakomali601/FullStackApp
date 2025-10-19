have to create mysql container first 

docker run -itd --name <container_name> --network <network_name> -e MYSQL_ROOT_PASSWORD=<customized_root_password> -e MYSQL_DATABASE=employee_db -e MYSQL_USER=<customized_user> -e MYSQL_PASS=<customized_password> -p 3306:3306 <imaged_name>

MYSQL_ROOT_PASSWORD create root password MYSQL_DATABASE create the databse is the mandatory environment variables  MYSQL_USER, MYSQL_PASS creates user and password these variables we have to ensure based on values given in application.properties file during the creation of container we are passign the values
