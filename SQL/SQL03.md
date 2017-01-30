##SQL CHECK Constraint
CHECK Constraint는 열에 배치 할 수 있는 값 범위를 제한하는데 사용
단일 열에 CHECK Constraint를 정의하면이 열에 대해 특정 값만 허용
테이블에 CHECK Constraint를 정의하면 행의 다른 열에있는 값을 기반으로 특정 열의 값을 제한 가능

##SQL DEFAULT Constraint
DEFAULT Constraint는 열에 기본값을 삽입하는 데 사용
다른 값을 지정하지 않으면 dafault값이 모든 새 레코드에 추가

##SQL CREATE INDEX
create index는 테이블에 인덱스를 만드는데 사용
테이블에 index를 생성하여 보다 빠르고 효율적으로 데이터 찾을 수 있음
사용자는 index를 볼 수 없고, 검색/쿼리 속도를 높이기 위해 사용

		CREATE INDEX index_name
		ON table_name (column_name)
		테이블에 index를 작성 (중복값 사용가능)
		
		CREATE UNIQUE INDEX index_name
		ON table_name (column_name)
		테이블에 고유 index를 작성 (중복 값은 허용되지 않음)
		
		CREATE INDEX PIndex
		ON Persons (LastName)
		Persons 테이블에서 LastName열에 PIndex를 생성
		
		CREATE INDEX PIndex
		ON Persons (LastName, FirstName)
		index를 쉼표로 구분해 괄호 안에서 열이름 나열 할 수 있음


##SQL DROP INDEX, DROP TABLE, and DROP DATABASE
drop으로 index, 테이블, 데이터베이스를 쉽게 제거/삭제 할 수 있음

		DROP TABLE table_name
		테이블 삭제
		
		DROP DATABASE database_name
		데이터베이스 삭제
		
		TRUNCATE TABLE table_name


##SQL ALTER TABLE
ALTER TABLE은 기존 테이블에 열을 추가, 삭제 또는 수정하는데 사용

		ALTER TABLE table_name
		ADD column_name datatype
		테이블에 열추가
		
		ALTER TABLE table_name
		DROP COLUMN column_name
		테이블에 열 삭제삭

##SQL AUTO INCREMENT Field
AUTO INCREMENT는 새로운 레코드가 테이블에 삽입되면 고유번호 생성
새 레코드가 삽입 될 때마다 primary key 필드의 값을 자동으로 생성하는 것이 좋다.

##SQL VIEWS
view는 가상 테이블
view는 실제 테이블처럼 행과 열이 포함
view의 필드는 데이터베이스에 있는 하나 이상의 실제 테이블의 필드

		CREATE VIEW view_name AS
		SELECT column_name(s)
		FROM table_name
		WHERE condition

		CREATE OR REPLACE VIEW view_name AS
		SELECT column_name(s)
		FROM table_name
		WHERE condition

		CREATE OR REPLACE VIEW [Current Product List] AS
		SELECT ProductID,ProductName,Category
		FROM Products
		WHERE Discontinued=No

##SQL Dates

* 날짜 데이터 형식(MySQL)
	* DATE - 형식 YYYY-MM-DD
	* DATETIME - 형식 : YYYY-MM-DD HH : MI : SS
	* TIMESTAMP - 형식 : YYYY-MM-DD HH : MI : SS
	* YEAR - 형식 YYYY 또는 YY
* 날짜 데이터 형식(MySQL)
	* DATE - 형식 YYYY-MM-DD
	* DATETIME - 형식 : YYYY-MM-DD HH : MI : SS
	* SMALLDATETIME - 형식 : YYYY-MM-DD HH : MI : SS
	* TIMESTAMP - 형식 : 고유 번호

##SQL NULL Values
NULL Values 알수 없는 누락된 데이터를 나타냄
기본적으로 테이블의 열은 NULL Values를 저장 가능
테이블의 열이 선택적이면 열에 값을 추가하지 않고 새 레코드를 삽입하거나 기존 레코드를 업데이트 할 수 있다
>NULL과 0을 비교하는것은 불가능

		SELECT LastName,FirstName,Address FROM Persons
		WHERE Address IS NULL
		Address열에 NULL값만 레코드를 선택

		SELECT LastName,FirstName,Address FROM Persons
		WHERE Address IS NOT NULL
		Address열에 없는 NULL값을 가진 레코드만 선택

##SQL 일반 데이터 유형
|Data type|Description|
|---|---|
|CHARACTER(n)|Character string. Fixed-length n|
|VARCHAR(n) or CHARACTER VARYING(n)|Character string. Variable length. Maximum length n|
|BINARY(n)|Binary string. Fixed-length n|
|BOOLEAN|Stores TRUE or FALSE values|
|VARBINARY(n) or BINARY VARYING(n)|Binary string. Variable length. Maximum length n|
INTEGER(p)|Integer numerical (no decimal). Precision p|
|SMALLINT|Integer numerical (no decimal). Precision 5|
INTEGER|Integer numerical (no decimal). Precision 10|
|BIGINT|Integer numerical (no decimal). Precision 19|
|DECIMAL(p,s)|Exact numerical, precision p, scale s. Example: decimal(5,2) is a number that has 3 digits before the decimal and 2 digits after the decimal|
||NUMERIC(p,s)|Exact numerical, precision p, scale s. (Same as DECIMAL)|
|FLOAT(p)|Approximate numerical, mantissa precision p. A floating number in base 10 exponential notation. The size argument for this type consists of a single number specifying the minimum precision|
|REAL|Approximate numerical, mantissa precision 7|
|FLOAT|Approximate numerical, mantissa precision 16|
|DOUBLE PRECISION|Approximate numerical, mantissa precision 16|
|DATE|Stores year, month, and day values|
TIME|Stores hour, minute, and second values|
|TIMESTAMP|Stores year, month, day, hour, minute, and second values|
|INTERVAL|Composed of a number of integer fields, representing a period of time, depending on the type of interval|
|ARRAY|A set-length and ordered collection of elements|
|MULTISET|A variable-length and unordered collection of elements|
|XML|Stores XML data|
