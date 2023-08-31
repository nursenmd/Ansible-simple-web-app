# Simple Web Application

This web application uses [Python Flask](http://flask.pocoo.org/) and [MySQL](https://www.mysql.com/) database. 
This demonstration is for the development of Ansible Playbooks.
  
Require steps to get this workable on a Linux system.
  
  > Install all required dependencies
  > Install and Configure Database
  > Start Database Service
  > Install and Configure the Web Server
  > Start Web Server
   
## 1. Install all required dependencies
  
  Python and its dependencies

    sudo apt-get install -y python3 python3-setuptools python3-dev build-essential python3-pip python3-mysqldb

   
## 2. Install and Configure Database
    
 Install MySQL database
    
    apt-get install -y mysql-server mysql-client

## 3. Start Database Service
  - Start the database service
    
        service mysql start

  - Create database and database users
        
        # mysql -u <username> -p
        
        mysql> CREATE DATABASE employee_db;
        mysql> GRANT ALL ON *.* to db_user@'%' IDENTIFIED BY 'Passw0rd';
        mysql> USE employee_db;
        mysql> CREATE TABLE employees (name VARCHAR(20));
        
  - Insert some test data
        
        mysql> INSERT INTO employees VALUES ('nur');
    
## 4. Install and Configure Web Server

Install Python Flask dependency

    pip install flask
    pip install flask-mysql

- Copy app.py or download it from source repository
- Configure database credentials and parameters 

## 5. Start Web Server

Start web server

    FLASK_APP=app.py flask run --host=0.0.0.0
    
## 6. Test

Open a browser and go to URL

    http://<IP>:5000                            => Welcome
    http://<IP>:5000/how%20are%20you            => I am good, how about you?
    http://<IP>:5000/read%20from%20database     => JOHN
