##SQL 조인(Joins)
두개 이상의 테이블에서 행을 결합시키는데 사용

		SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
		FROM Orders
		INNER JOIN Customers
		ON Orders.CustomerID=Customers.CustomerID;
		Orders테이블의 OrderID항목과 Customers테이블의 CustomerName항목,
		Orders테이블의OrderDate를 
		
##SQL 내부조인(INNER JOIN)
Inner는 

		SELECT column_name(s)
		FROM table1
		INNER JOIN table2
		ON table1.column_name=table2.column_name;

or

		SELECT column_name(s)
		FROM table1
		JOIN table2
		ON table1.column_name=table2.column_name;

![](http://www.w3schools.com/sql/img_innerjoin.gif) 

		SELECT Customers.CustomerName, Orders.OrderID
		FROM Customers
		INNER JOIN Orders
		ON Customers.CustomerID=Orders.CustomerID
		ORDER BY Customers.CustomerName;
		모든Customers와 함께 Orders를 반환합니다

##sQL LEFT JOIN
LEFT는 

		SELECT column_name(s)
		FROM table1
		LEFT JOIN table2
		ON table1.column_name=table2.column_name;

or

		SELECT column_name(s)
		FROM table1
		LEFT OUTER JOIN table2
		ON table1.column_name=table2.column_name;

![](http://www.w3schools.com/sql/img_leftjoin.gif) 

		SELECT Customers.CustomerName, Orders.OrderID
		FROM Customers
		LEFT JOIN Orders
		ON Customers.CustomerID=Orders.CustomerID
		ORDER BY Customers.CustomerName;
		
##SQL RIGHT JOIN


		SELECT column_name(s)
		FROM table1
		RIGHT JOIN table2
		ON table1.column_name=table2.column_name;

or

		SELECT column_name(s)
		FROM table1
		RIGHT OUTER JOIN table2
		ON table1.column_name=table2.column_name;

![](http://www.w3schools.com/sql/img_rightjoin.gif) 

		SELECT Orders.OrderID, Employees.FirstName
		FROM Orders
		RIGHT JOIN Employees
		ON Orders.EmployeeID=Employees.EmployeeID
		ORDER BY Orders.OrderID;
		
##SQL FULL OUTER JOIN


		SELECT column_name(s)
		FROM table1
		FULL OUTER JOIN table2
		ON table1.column_name=table2.column_name;

![](http://www.w3schools.com/sql/img_fulljoin.gif)

		SELECT Customers.CustomerName, Orders.OrderID
		FROM Customers
		FULL OUTER JOIN Orders
		ON Customers.CustomerID=Orders.CustomerID
		ORDER BY Customers.CustomerName;
		
##SQL UNION
UNION은 두개 이상의 SELECT의 결과 집합을 결합하는데 사용
UNION내의 각 SELECT는 동일한 수의 열, 유사한 데이터형식이 있어야 한다.

		SELECT column_name(s) FROM table1
		UNION
		SELECT column_name(s) FROM table2;

		UNION연산자는 기본적으로 별개의 값을 선택
		중복 값을 허용하려면 UNION 과 ALL을 사용
		
		SELECT column_name(s) FROM table1
		UNION ALL
		SELECT column_name(s) FROM table2;
--
	
		SELECT City FROM Customers
		UNION
		SELECT City FROM Suppliers
		ORDER BY City;
		
		Customers, Suppliers 테이블에서 모든 다른 도시들을 선택
--

		SELECT City FROM Customers
		UNION ALL
		SELECT City FROM Suppliers
		ORDER BY City;
		
		Customers, Suppliers 테이블에서 모든 도시들을 선택
--

		SELECT City, Country FROM Customers
		WHERE Country='Germany'
		UNION ALL
		SELECT City, Country FROM Suppliers
		WHERE Country='Germany'
		ORDER BY City;
		
		UNION ALL을 사용하여 "Customers"및 "Suppliers"테이블에서 모든 독일 도시를 선택

##SQL SELECT INTO
테이블에서 다른 것으로 정보를 복사 할 수 있다
SELECT INTO는 하나의 테이블에서 데이터를 선택하고 새 테이블에 삽입

		SELECT *
		INTO newtable [IN externaldb]
		FROM table1;

		새로운 테이블에 모든 열 복사
--

		SELECT column_name(s)
		INTO newtable [IN externaldb]
		FROM table1;
		
		원하는 열만 새테이블에 복사 할 수 있다.

##SQL INSERT INTO SELECT
SELECT INSERT INTO 문은 하나의 테이블에서 데이터를 선택하고 기존 테이블에 삽입
목표 테이블의 기존 행이 영향을받지 않는다.

		INSERT INTO table2
		SELECT * FROM table1;
		
		테이블에 기존 테이블의 모든 열을 복사
--

		INSERT INTO table2
		(column_name(s))
		SELECT column_name(s)
		FROM table1;
		
		우리가 원하는 열에 기존 테이블을 복사 할 수 있다

##SQL CREATE DATABASE
CREATE DATABASE 문은 데이터베이스를 만드는 데 사용

		CREATE DATABASE my_db;
		
		my_db라는 데이터베이스를 생성

##SQL CREATE TABLE
CREATE TABLE 문은 데이터베이스에서 테이블을 만드는 데 사용
테이블은 행과 열로 구성
각 테이블은 이름이 있어야 함

		CREATE TABLE table_name
		(
		column_name1 data_type(size),
		column_name2 data_type(size),
		column_name3 data_type(size),
		....
		);

		COLUMN_NAME 은 테이블 컬럼의 이름을 지정
		DATA_TYPE 은 열이 저장할 수 있는 데이터(예: VARCHAR, 정수, 소수, 날짜)의 유형을 지정
		size는 테이블 열의 최대 길이를 지정

##SQL 제약조건(CONSTRAINT)
데이터에 대한 규칙을 지정하기 위해 사용
제약 조건 및 데이터간의 동작 위반이 있는 경우 동작은 제한에 의해 중단

		CREATE TABLE table_name
		(
		column_name1 data_type(size) constraint_name,
		column_name2 data_type(size) constraint_name,
		column_name3 data_type(size) constraint_name,
		....
		);

* NOT NULL - 열이 NULL 값을 저장할 수 없음을 나타냄
* UNIQUE - 중복되는 값이 오면 안됨
* PRIMARY KEY - 그 사람만이 가지고 잇는 고유값(NOT NULL + UNIQUE)
* FOREIGN KEY - 다른 테이블의 값과 일치하는 하나의 테이블에서 데이터의 참조 무결성을 보장
* CHECK - 열의 값이 특정 조건을 충족 보장
* DEFAULT - 열에 대한 디폴트 값을 지정


##SQL NOT NULL
NOT NULL 제약 조건은 열이 NULL 값을 허용하지 않도록 강제
NOT NULL 제약 조건은 필드가 항상 값을 포함하도록 함
즉, 새 레코드를 삽입하거나이 필드에 값을 추가하지 않으면 레코드를 업데이트 할 수 없습니다.

		CREATE TABLE PersonsNotNull
		(
		P_Id int NOT NULL,
		LastName varchar(255) NOT NULL,
		FirstName varchar(255),
		Address varchar(255),
		City varchar(255)
		)

##SQL UNIQUE
UNIQUE는 데이터베이스 테이블의 각 레코드를 고유하게 식별
UNIQUE 및 PRIMARY KEY는 둘 다 열 또는 열 집합의 고유성을 보장
PRIMARY KEY에는 자동으로 UNIQUE가 정의되어 있습니다.
테이블에는 여러개의 UNIQUE가 있을수 있지만 PRIMARY KEY는 한개만 존재

##SQL PRIMARY KEY
PRIMARY KEY는 데이터베이스 테이블의 각 레코드를 고유하게 식별
PRIMARY Keys는 UNIQUE값을 포함
NULL값을 포함 할 수 없음
대부분의 테이블은 Primary key를 가지고 있고, 각 테이블은 하나의 primary key를 가질 수 있다.

##SQL FOREIGN KEY
한 테이블의 FOREIGN KEY는 다른 테이블의 PRIMARY KEY를 가리킴
