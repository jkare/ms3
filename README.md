# ms3
This is a contact management API. It connects to MySQL database and supports CRUD operations. below is the list of apis.
```
customers
  GET: http://customersampleapi.us-e2.cloudhub.io/api/customers
  POST: http://customersampleapi.us-e2.cloudhub.io/api/customers
customer
  GET: http://customersampleapi.us-e2.cloudhub.io/api/customers/1
  PUT: http://customersampleapi.us-e2.cloudhub.io/api/customers/1
  DELETE: http://customersampleapi.us-e2.cloudhub.io/api/customers/1
  
addresses
  GET: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/addresses
  POST: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/addresses
address
  GET: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/addresses/1
  PUT: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/addresses/1
  DELETE: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/addresses/1
  
contacts
  GET: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/contacts
  POST: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/contacts
contact
  GET: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/contacts/1
  PUT: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/contacts/1
  DELETE: http://customersampleapi.us-e2.cloudhub.io/api/customers/1/contacts/1
```
Database scripts
```
CREATE TABLE `CUSTOMER` (
  `ID` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `FIRSTNAME` varchar(50) NOT NULL DEFAULT '',
  `LASTNAME` varchar(50) NOT NULL DEFAULT '',
  `DOB` date NOT NULL,
  `GENDER` varchar(1) DEFAULT NULL,
  `TITLE` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`ID`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;

CREATE TABLE `ADDRESS` (
  `ID` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `CUSTOMERID` int(11) unsigned NOT NULL,
  `TYPE` varchar(20) DEFAULT '',
  `NUMBER` varchar(50) NOT NULL DEFAULT '',
  `STREET` varchar(50) NOT NULL DEFAULT '',
  `UNIT` varchar(50) DEFAULT NULL,
  `CITY` varchar(50) DEFAULT NULL,
  `STATE` varchar(50) DEFAULT NULL,
  `ZIPCODE` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`ID`),
  KEY `CUSTOMER_ADDRESS_FKEY` (`CUSTOMERID`),
  CONSTRAINT `CUSTOMER_ADDRESS_FKEY` FOREIGN KEY (`CUSTOMERID`) REFERENCES `CUSTOMER` (`ID`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;

CREATE TABLE `CONTACT` (
  `ID` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `CUSTOMERID` int(11) unsigned NOT NULL,
  `TYPE` varchar(50) DEFAULT '',
  `VALUE` varchar(50) NOT NULL DEFAULT '',
  `PREFERRED` tinyint(1) NOT NULL,
  PRIMARY KEY (`ID`),
  KEY `CUSTOMER_CONTACT_FK` (`CUSTOMERID`),
  CONSTRAINT `CUSTOMER_CONTACT_FK` FOREIGN KEY (`CUSTOMERID`) REFERENCES `CUSTOMER` (`ID`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;
```

![alt text](https://github.com/jkare/ms3/blob/master/DB_schema.png "DB Schema")



