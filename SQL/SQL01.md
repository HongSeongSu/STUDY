# SQL(Structured Query Language)
###1. SQL 이란?
SQL은 액세스하고 데이터베이스를 조작하기 위한 표준언어.

* 구조적 쿼리 언어
* 데이터베이스에 접근하고 조작 가능
* ANSI(American National Standards Insitute) 표준

####SQL이 할 수 있는것
* 데이터베이스에 대해 쿼리 실행 가능
* 데이터베이스에서 데이터 검색 가능
* 데이터베이스에 레코드 삽입 가능
* 데이터베이스에 레코드 업데이트 가능
* 새로운 데이터베이스 생성 가능
* 데이터베이스에서 새로운 테이블 생성 가능

#####SQL은 표준이지만 다른 SQL버전이 있습니다. 그러나 ANSI 표준을 준수하기 위해 이들은 모두 SELECT, UPDATE, DELETE, INSERT, WHERE와 같은 주요 명령을 비슷한 방식으로 지원합니다.

####RDBMS(Relational Database Management System)
* RDBMS는 관계형 데이터베이스 관리 시스템.
* RDBMS는 SQL과 MS SQL Server, IBM DB2, Oracle, MySQL 및 Microsoft Access와 같은 모든 최신 데이터베이스 시스템의 기초
* RDBMS의 데이터는 테이블이라느 데이터베이스 오브젝트에 저장
* 테이블은 관련 데이터 항목의 모음이며 행과 열로 구성

<hr>
##Database Tables
데이터베이스는 대게 하나 이상의 테이블을 포함한다. 각 테이블은 이름으로 식별된다. 테이블은 데이터가 있는 레코드(행)을 포함한다.

>SQL 키워드는 대소 문자를 구분하지 않는다. (select = SELECT)

##SQL 문 다음에 오는 세미콜론?
일부 데이터베이스 시스템에서는 각 SQL문의 끝에 세미콜론이 필요
세미콜론은 데이터베이스 시스템에서 각 SQL문을 분리하여 서버에 대한 동일한 호출에서 둘 이사의 SQL문을 실행 할 수 있도록하는 표준 방법

##중요한 SQL 명령 중 일부
* SELECT - 데이터베이스에서 데이터를 추출
* UPDATE - 데이터베이스에 데이터를 업데이트
* DELETE - 데이터베이스에서 데이터를 삭제
* INSERT INTO - 데이터베이스에 새로운 데이터를 삽입
* CREATE DATABASE - 새로운 데이터베이스를 만듬
* ALTER DATABASE - 데이터베이스를 수정
* CREATE TABLE - 새로운 테이블 만듬
* ALTER TABLE - 테이블을 수정
* DROP TABLE - 테이블을 삭제
* CREATE INDEX - 인덱스(검색 키)를 생성
* DROP INDEX - 인덱스를 삭제

<hr>

###SQL SELECT
SELECT는 데이터베이스에서 데이터를 선택하는데 사용됩니다.
결과는 결과세트라고 하는 테이블에 저장

###SQL SELECT 구문

		SELECT column_name, column_name
		FROM table_name;
		과
		SELECT * FROM table_name;
		
		table_name인 테이블에서 SELECT에 해당하는 데이터를 불러오는 것이다.
		
###SQL SELECT DISTINCT
테이블에서 열은 많은 중복 값을 포함 할 수 있습니다. 때로는 서로 다른 값만 나열하고한다.
DISTINCT 키워드는 고유한 값만 리턴하는데 사용될 수 있다.

		SELECT DISTINCT column_name, column_name
		FROM table_name;
		
		DISTINCT는 테이블에서 해당 열의 고유한 값만 선택한다.
		
###SQL WHERE
WHERE레코드를 필터링하는데 사용

		SELECT column_name, column_name
		FROM table_name
		WHERE column_name operator value;
		
		SELECT * FROM Customers
		WHERE Country='Mexico';
		
		Customers 테이블에서 Mexico국가의 모든 고객을 선택한다
		
		SQL은 텍스트 값에 대해 작은 따옴표를 사용해야한다
		(대부분의 데이터베이스 시스템은 큰따옴표도 허용)
		그러나 숫자 필드는 따옴표로 묶지 않아야 한다.
		
		SELECT * FROM Custmers
		WHERE CustomerID=1;
		
####WHERE에서 사용할 수 있는 연산자
|Operate|Description|
|---|---|
|=|같음|
|<>|같지않음|
|>|크다|
|<|작다|
|>=|크거나같다|
|<=|작거나같다|
|BETWEEN|두값 사이에 있다|
|LIKE|패턴검색|
|IN|열에 가능한 여러 값을 지정|


##SQL AND, OR 연산자
AND, OR 연산자는 둘 이상의 조건에 따라 레코드를 필터링하는데 사용

* AND 연산자는 첫번째 조건과 두번째 조건이 모두 참인경우 레코드 표시
* OR 연산자는 첫번째 조건과 두번째 조건 둘중 하나만 참이여도 레코드 표시

		SELECT * FROM Customers
		WHERE Country='Germany'
		AND City='Berlin';
		 
		Customers 테이블에서 Germany 과 Berlin 두도시의 모든 고객을 선택
	<hr>

		SELECT * FROM Customers
		WHERE City='Berlin'
		OR City='München';
		
		Customers 테이블에서 Berlin 또는 München의 모든 고객을 선택
	<hr>
	
		SELECT * FROM Customers
		WHERE Country='Germany'
		AND (City='Berlin' OR City='München');
		
		Customers 테이블에서 Germany의 고객을 선택하고 도시는 Berlin또는 München 같아야합니다
<hr>
##SQL ORDER BY

ORDER BY는 하나 이상의 열을 기준으로 결과 집합을 정렬하는 데 사용됩니다.

ORDER BY 키워드는 기본적으로 레코드를 오름차순으로 정렬합니다.
내림차순으로 레코드를 정렬하려면 DESC 키워드를 사용할 수 있습니다.

		SELECT column_name, column_name
		FROM table_name
		ORDER BY column_name ASC|DESC, column_name ASC|DESC;

<hr>

		SELECT * FROM Customers
		ORDER BY Country;

		Customers 테이블의 모든 고객을 Country 열로 정렬하여 선택

<hr>

		SELECT * FROM Customers
		ORDER BY Country DESC;

		Customers 테이블의 모든 고객을 Country 열에 의해 DESCENDING로 정렬하여 선택

<hr>

		SELECT * FROM Customers
		ORDER BY Country, CustomerName;

		Customers 테이블의 모든 고객을 Country 및 CustomerName 열로 정렬하여 선택

<hr>

		SELECT * FROM Customers
		ORDER BY Country ASC, CustomerName DESC;

		Customers테이블의 모든 고객을 국가에 따라 오름차순으로 정렬하고
		CustomerName 열로 내림차순으로 정렬

##SQL INSERT INTO
INSERT INTO는 테이블에 새 레코드를 삽입하는데 사용

		INSERT INTO table_name
		VALUES (value1,value2,value3,...);

		데이터가 삽입 될 열 이름을 지정하지 않고 값만 지정

<hr>

		INSERT INTO table_name (column1,column2,column3,...)
		VALUES (value1,value2,value3,...);

		열 이름과 삽입 할 값을 모두 지정

<hr>

		INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
		VALUES ('Cardinal','Tom B. Erichsen','Skagen 21','Stavanger','4006','Norway');

		Customers테이블에 새행을 삽입한다.

<hr>

		INSERT INTO Customers (CustomerName, City, Country)
		VALUES ('Cardinal', 'Stavanger', 'Norway');

		새 행을 삽입하지만 CustomerName, City및 Country열에만 데이터를 삽입합니다.
		(물론 CustomerID 필드도 자동으로 업데이트)

##SQL UPDATE

		UPDATE Customers
		SET City='Hamburg'
		WHERE CustomerID=1;

		Customers테이블에서 레코드의 도시열 값을 변경

UPDATE는 테이블의 기존 레코드를 업데이트하는데 사용

		UPDATE Customers
		SET ContactName='Alfred Schmidt', City='Frankfurt'
		WHERE CustomerID=1;

--

		UPDATE Customers
		SET ContactName='Juan'
		WHERE Country='Mexico';

		WHERE 절 : WHERE Country='Mexico'필드 값 멕시코가 모든 레코드를 업데이트

--

		UPDATE Customers
		SET ContactName='Juan';

		WHERE 절을 생략하면 모든 레코드가 업데이트됩니다.
		
###SQL DELETE
DELETE는 테이블의 행을 삭제하는데 사용

		DELETE FROM table_name
		WHERE some_column=some_value;

--

		DELETE FROM Customers
		WHERE CustomerName='Alfreds Futterkiste'
		AND ContactName='Maria Anders';
		
		Customers 테이블에서 고객 Alfreds Futterkiste를 삭제
		
--

		DELETE FROM table_name;

		or

		DELETE * FROM table_name;
		
		테이블을 삭제하지 않고 테이블의 모든 행을 삭제 할 수 있다.
		이것은 테이블 구조, 속성 및 인덱스가 손상되지 않는다는 것을 의미

<hr>
##SQL Injection
SQL Injection은 데이터베이스를 파괴할수 있다.
SQL Injection은 사용자가 악의적으로 웹페이지에 입력을 통해 SQL 명령문에 SQL명령을 주입 할 수있는 기술
삽입된 SQL명령은 SQL을 변경하고 웹응용프로그램의 보안을 손상시킬 수 있다.

1=1의 SQL 삽입은 항상 참이 된다

		SELECT * FROM Users WHERE UserId = 105 or 1=1;
		
		WHERE 1=1 항상 참이기 때문에 테이블에서 모든 행을 반환한다.
		
		SELECT UserId, Name, Password FROM Users WHERE UserId = 105 or 1=1;
		
		105 or 1=1을 입력하기만 하면 데이터베이스의 모든 사용자 이름과 암호에 접근 가능


##SQL SELECT TOP
SELECT TOP은 리턴할 레코드 수를 지정하는데 사용
SELECT TOP은 수천개의 레코드가 있는 큰 테이블에서 매우 유용 할 수 있다.
많은 수의 레코드를 반환하는 성능에 영향을 줄 수 있다.

		SELECT TOP 2 * FROM Customers;
		Customers 테이블에서이 첫 번째 레코드를 선택
		
		SELECT TOP 50 PERCENT * FROM Customers;
		Customers 테이블에서 레코드의 첫 번째 50 %를 선택
		
##SQL LIKE
LIKE 연산자는 열에서 특정 패턴을 검색하는 데 사용

		SELECT column_name(s)
		FROM table_name
		WHERE column_name LIKE pattern;
		--------
		SELECT * FROM Customers
		WHERE City LIKE 's%';
		문자 S로 시작하는 모든 고객을 선택
		--------
		SELECT * FROM Customers
		WHERE City LIKE '%s';
		문자 "S"로 끝나는 모든 고객을 선택
		---------
		SELECT * FROM Customers
		WHERE Country LIKE '%land%';
		패턴 lands를 포함하는 모든 고객을 선택
		---------
		SELECT * FROM Customers
		WHERE Country NOT LIKE '%land%';
		패턴 lands를 포함하하지 않는 모든 고객을 선택
		
##SQL 와일드 카드
와일드카드 문자는 문자열의 다른 문자들을 대체하는데 사용
SQL에서 와일드 카드 문자는 SQL LIKE 연산자와 함께 사용
SQL 와일드 카드 테이블 내의 데이터를 검색하기 위해 사용

|와일드카드|Description|
|---|---|
|%|0개 이상의 문자를 대체 할 수 있다|
|_|단일문자 대신 사용할 수 있는 문자|
|[charlist]|일치시킬 문자의 집합 및 범위|
|[^charlist]or[!charlist]|괄호안에 지정되지 않은 문자만 일치시킴|

		SELECT * FROM Customers
		WHERE City LIKE 'ber%';
		BER로 시작하는 모든 고객을 선택
		-------
		SELECT * FROM Customers
		WHERE City LIKE '%es%';
		ES패턴을 포함하는 모든 고객을 선택
		-------
		SELECT * FROM Customers
		WHERE City LIKE '_erlin';
		erlin 다음에 어떤 문자로 시작하는 모든 고객을 선택
		-------
		SELECT * FROM Customers
		WHERE City LIKE 'L_n_on';
		City에서 L로 시작하고 n다음에 어떤 문자던지 on다음에 어떤 문자던지 오는 모든 고객을 선택
		-------
		SELECT * FROM Customers
		WHERE City LIKE '[bsp]%';
		City에서 b,s,p로 시작하는 모든 고객을 선택
		--------
		SELECT * FROM Customers
		WHERE City LIKE '[a-c]%';
		City에서 a,b,c로 시작하는 모든 고객을 선택
		--------
		SELECT * FROM Customers
		WHERE City LIKE '[a-c]%';
		or
		SELECT * FROM Customers
		WHERE City NOT LIKE '[bsp]%';
		City에서 b,s,p로 시작하지 않는 모든 고객을 선택


##SQL IN
IN을 사용하면 WHERE에 여러 값을 지정 할 수 있음

		SELECT column_name(s)
		FROM table_name
		WHERE column_name IN (value1,value2,...);
--
		SELECT * FROM Customers
		WHERE City IN ('Paris','London');
		Pairs 또는 London의 모든 고객을 선택
		
##SQL BETWEEN
BETWEEN 은 범위내에서 값을 선택하는데 사용

		SELECT column_name(s)
		FROM table_name
		WHERE column_name BETWEEN value1 AND value2;
--
		
		SELECT * FROM Products
		WHERE Price BETWEEN 10 AND 20;
		10에서 20사이의 모든 가격의 Product를 선택
--
		
		SELECT * FROM Products
		WHERE Price NOT BETWEEN 10 AND 20;
		10에서 20사이의 가격이 아닌 모든 제품을 선택
--
		
		SELECT * FROM Products
		WHERE (Price BETWEEN 10 AND 20)
		AND NOT CategoryID IN (1,2,3);
		10에서 20사이의 제품을 표시하지만 CategoryID가 1,2,3인 제품은 표시 하지 않음
--
		
		SELECT * FROM Products
		WHERE ProductName BETWEEN 'C' AND 'M';
		C와 M으로 시작하는 모든 제품을 선택
--
		
		SELECT * FROM Products
		WHERE ProductName NOT BETWEEN 'C' AND 'M';
		C와M으로 시작하지 않는 모든 제품을 선택
--
		
		SELECT * FROM Orders
		WHERE OrderDate BETWEEN #07/04/1996# AND #07/09/1996#;
		1996년 7월 4일 ~ 1996년 7월 9일 사이의 모든 주문을 선택

##SQL 별칭(Aliases)
SQL Aliases는 열의 이름이나 테이블이름이 길거나 특수문자가 포함된 경우 짧고 쉬운 이름으로 대체할 수 있다

		SELECT column_name AS alias_name
		FROM table_name;
--

		SELECT column_name(s)
		FROM table_name AS alias_name;
--

		SELECT CustomerName AS Customer, ContactName AS [Contact Person]
		FROM Customers;
		Customer, ContactName을 하나의 열로 묶는다
--
		
		SELECT CustomerName, Address+', '+City+', '+PostalCode+', '+Country AS Address
		FROM Customers;
		Address, City, PostalCode, Country를 Adress라는 하나로 묶는다
--

		SELECT o.OrderID, o.OrderDate, c.CustomerName
		FROM Customers AS c, Orders AS o
		WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID;
		
		not aliases
		SELECT Orders.OrderID, Orders.OrderDate, Customers.CustomerName
		FROM Customers, Orders
		WHERE Customers.CustomerName="Around the Horn" AND Customers.CustomerID=Orders.CustomerID;
		
