*have to create mysql container first 

docker run -itd --name <container_name> --network <network_name> -e MYSQL_ROOT_PASSWORD=<customized_root_password> -e MYSQL_DATABASE=<<created_db_name> -e MYSQL_USER=<customized_user> -e MYSQL_PASS=<customized_password> -p 3306:3306 <imaged_name>

MYSQL_ROOT_PASSWORD create root password MYSQL_DATABASE create the databse is the mandatory environment variables  MYSQL_USER, MYSQL_PASS creates user and password these variables we have to ensure based on values given in application.properties file during the creation of container we are passign the values, once its strated it shows ready for the connection in logs

*next we have to create the backnend application 

docker run -itd --name <container_name> --network <network_name> -p <host_port>:<default_port> -e MSQLSRV_URL=jdbc:mysql//<mysql_container_name>:3306/<created_db_name> -e MYSQL_USER=<customized_user> -e MYSQL_PASS=<customized_password> <backendapp_created_image>

<host_port>:<default_port>
    host_port : in which we have to access the application
    default_port: in which container actually running, this one also we have to give in application.properties file
    
MSQLSRV_URL=jdbc:mysql//<mysql_container_name>:3306/<created_db_name>
    MSQLSRV_URL = environment varibale to mention the mysql url, it is the url to connect mysql server

*next we have to create frontend application

docker run -itd --name <container_name> --network ownbridge -p <host_port>:<default_port> <frontend_created_image>

default port we have to given in Dockerfile

*in Employeecontroller.jave we have to give exact port of frontend how we are accessing and have to give trough which api we are access the backend application, like below

<img width="1055" height="580" alt="image" src="https://github.com/user-attachments/assets/9ab7bc52-7939-421d-878f-2b49318890a0" />

*In App.js we have to give backend url how we ae accessing
http://localhost:9090/api/employees

<img width="902" height="880" alt="image" src="https://github.com/user-attachments/assets/901efd10-adcb-4895-bf8b-877e9d89d5f9" />

NOTE: All container should be in the same network

