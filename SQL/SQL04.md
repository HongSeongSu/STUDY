##SQL 집계 함수
SQL 집계 함수는 열의 값에서 계산 한 값을 반환

* AVG는 () - 평균 값을 반환
* COUNT (가) - 행의 수를 돌려줍니다
* FIRST는 () - 첫 번째 값을 반환
* () LAST는 - 마지막 값을 반환
* MAX는 () - 가장 큰 값을 반환
* MIN은 () - 가장 작은 값을 반환
* SUM은 () - 합을 반환

##SQL 스칼라 함수
 SQL 스칼라 함수는 입력 값에 기초하여 하나의 값을 반환한다.

* UCASE ()는이 - 대문자로 필드로 변환
* LCASE ()는이 - 소문자 할 수있는 필드로 변환
* MID () - 텍스트 필드에서 추출 문자
* LEN은 ()는 - 텍스트 필드의 길이를 반환
* 라운드 () - 지정된 소수점 수를 숫자 필드 반올림
* NOW () - 현재 시스템 날짜 및 시간을 반환
* FORMAT () - 포맷 필드가 표시되는 방법

###AVG()
AVG()는 숫자 열의 평균 값을 반환

		SELECT AVG(column_name) FROM table_name
		
		SELECT AVG(Price) AS PriceAverage FROM Products;
		Products테이블에서 Price열의 평균을 가져옴

###COUNt()
COUNT()는 지정된 기준과 일치하는 행의 수를 반환

		SELECT COUNT(column_name) FROM table_name;
		지정된 열값의 개수를 반환(NULL값 계산되지 않음)
		
		SELECT COUNT(*) FROM table_name;
		테이블의 레코드 수를 반환
		
		SELECT COUNT(DISTINCT column_name) FROM table_name;
		지정된 열의 고유값의 수를 반환

###FIRST()
선택된 열의 첫번째 값을 반환

		SELECT FIRST(column_name) FROM table_name;
		
		SELECT FIRST(CustomerName) AS FirstCustomer FROM Customers;
		Customers테이블에서 CustomerName열의 첫번째 값을 선택
###LAST()
선택된 컬럼의 마지막 값을 반환

		SELECT LAST(column_name) FROM table_name;

		SELECT LAST(CustomerName) AS LastCustomer FROM Customers;
		Customers테이블에서 CustomerName열의 마지막 값을 선택
###MAX()
선택된 열의 가장 큰 값을 반환

		SELECT MAX(column_name) FROM table_name;
		
###MIN()
선택된 열의 가장 작은 값을 반환

		SELECT MIN(column_name) FROM table_name;

###SUM()
숫자 열의 총 합을 반환

		SELECT SUM(column_name) FROM table_name;

##SQL GROUP BY
GROUP BY문은 집계 함수와 함께 사용되어 결과 집합을 하나 이상의 열로 그룹화합니다.

		SELECT column_name, aggregate_function(column_name)
		FROM table_name
		WHERE column_name operator value
		GROUP BY column_name;

##SQL HAVING
WHERE을 집계함수와 함께 사용할수 없어서 추가

		SELECT column_name, aggregate_function(column_name)
		FROM table_name
		WHERE column_name operator value
		GROUP BY column_name
		HAVING aggregate_function(column_name) operator value;

###UCASE ()
대문자 필드의 값을 변환

		SELECT UCASE(column_name) FROM table_name

##LCASE ()
소문자 필드의 값을 변환

		SELECT LCASE(column_name) FROM table_name;

##MID ()
텍스트 필드에서 문자를 추출하는 데 사용

		SELECT MID(column_name,start,length) AS some_name FROM table_name;

##LEN ()
텍스트 필드에있는 값의 길이를 반환

		SELECT LEN(column_name) FROM table_name;

##ROUND ()
지정된 소수점 수를 숫자 필드를 둥글게하기 위해 사용

		SELECT ROUND(column_name,decimals) FROM table_name;

##NOW ()
현재 시스템 날짜 및 시간을 반환한다.

		SELECT NOW() FROM table_name;

##FORMAT ()
필드가 디스플레이되는 방법을 형식화하기 위해 사용

		SELECT FORMAT(column_name,format) FROM table_name;

