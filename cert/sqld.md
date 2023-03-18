# SQL

## 관계형 데이터베이스(Relation Database)

### 관계형 데이터베이스의 등장

- 1970년대 E.F. Codd 박사의 논문에서 처음 소개된 데이터베이스
- 릴레이션(Relation)과 릴레이션의 조인 연산을 통해서 합집합, 교집합, 차집합 등을 만들 수 있다
- Oracle, MS-SQL, MySQL, Sybase 등의 다양한 데이터베이스 관리 시스템이 있다

### 데이터베이스와 데이터베이스 관리 시스템의 차이점

- 데이터베이스는 데이터를 어떠한 형태의 자료구조(Data Structure)로 사용하느냐에 따라서 나누어진다
- 데이터베이스의 종류는 계층형, 네트워크형, 관계형 데이터베이스 등이 있다
- 계층형은 트리(Tree) 형태의 자료구조에 데이터를 저장하고 관리하며, 네트워크는 오너(Owner)와 멤버(Member) 형태로 데이터를 저장한다
- 계층형은 1대N 관계를 표현한다
- 네트워크는 1대N과 함께 M대N 표현도 가능하다
- 관계형은 릴레이션에 데이터를 저장하고 관리한다
- 릴레이션을 사용해서 집합 연산과 관계 연산을 할 수 있다
- 데이터베이스 관리 시스템(Database Management System)은 계층형,네트워크, 관계형 데이터베이스 등을 관리하기 위한 소프트웨어를 의미하며, 일명 DBMS라고 한다
- DBMS의 종류에는 Oracle, MS-SQL, MySQL, Sybase 등이 있으며 모두 관계형 데이터베이스를 지원한다

### 집합 연산

| 합집합(Union) | - 두 개의 릴레이션을 하나로 합하는 것이다
- 중복된 행(튜플)은 한 번만 조회된다 |
| --- | --- |
| 차집합(Difference) | 본래 릴레이션에는 존재하고 다른 릴레이션에는 존재하지 않는 것을 조회한다 |
| 교집합(Intersection) | 두 개의 릴레이션 간에 공통된 것을 조회한다 |
| 곱집합(Cartesian product) | 각 릴레이션에 존재하는 모든 데이터를 조합하여 연산한다 |

### 관계 연산

| 선택 연산(Selection) | 릴레이션에서 조건에 맞는 행(튜플)만을 조회한다 |
| --- | --- |
| 투영 연산(Projection) | 릴레이션에서 조건에 맞는 속성만을 조회한다 |
| 결합 연산(Join) | 여러 릴레이션의 공통된 속성을 사용해서 새로운 릴레이션을 만들어 낸다 |
| 나누기 연산(Division) | 기준 릴레이션에서 나누는 릴레이션이 가지고 있는 속성과 동일한 값을 가지는 행(튜플)을 추출하고 나누는 릴레이션의 속성을 삭제한 후 중복된 행을 제거하는 연산이다 |

### 테이블(Table)의 구조

- 관계형 데이터베이스는 릴레이션에 데이터를 저장하고 릴레이션을 사용해서 집합 연산 및 관계 연산을 지원하여 다양한 형태로 데이터를 조회할 수 있다
- 릴레이션은 최종적으로 데이터베이스 관리 시스템에서 테이블(Table)로 만들어진다
- 기본키(Primary key)는 하나의 테이블에서 유일성(Unique)과 최소성, Not Null 을 만족하면서 해당 테이블을 대표하는 것이다. 그중에서 행(ROW)은 하나의 테이블에 저장되는 값으로 튜플(Tuple)이라고도 한다
- 컬럼(Column)은 어떤 데이터를 저장하기 위한 필드(Field)로 속성(Attribute)이라고도 한다
- 외래키(Foreign key)는 다른 테이블의 기본키를 참조(조인)하는 컬럼이다.
- 외래키는 관계 연산 중에서 결합 연산(Join)을 하기 위해서 사용한다

### SQL(Structured Query Language)

- SQL은 관계형 데이터베이스에 대해서 데이터의 구조를 정의, 데이터 조작, 데이터 제어 등을 할 수 있는 절차형 언어
- 관계형 데이터베이스는 데이터베이스를 연결하고 SQL문을 사용하여 데이터베이스를 누구나 쉽게 사용할 수 있도록 한다

### SQL 종류

| DDL(Data Definition Language) | - 관계형 데이터베이스의 구조를 정의하는 언어이다
- CREATE, ALTER, DROP, RENAME, TRUNCATE |
| --- | --- |
| DML(Data Manipulation Language) | - 테이블에서 데이터를 입력, 수정, 삭제, 조회
- INSERT, UPDATE, DELETE, SELECT |
| DCL(Data Control Language) | - 데이터베이스 사용자에게 권한을 부여하거나 회수한다
- GRANT, REVOKE |
| TCL(Transaction Control Language) | - 트랜잭션을 제어하는 명령어
- COMMIT, ROLLBACK, SAVEPOINT |
- DDL문은 데이터베이스 테이블을 생성하거나 변경, 삭제하는 것으로 데이터를 저장할 구조를 정의하는 언어이다
- DML은 데이터 구조가 DDL로 정의되면 해당 데이터 구조에 데이터를 입력하거나 수정, 삭제, 조회할 수 있다
- DCL은 DDL로 정의된 구조에 어떤 사용자가 접근할 수 있는지 권한을 부여하는 것이다
- 사용자에게 권한을 부여하고 권한이 부여되면 DDL로 데이터 구조를 정의한다
- 데이터 구조가 정의되면 데이터를 입력한 후에 개발자 및 사용자가 그 데이터를 조회하는 것이다

### 트랜잭션(Transaction)

- 트랜잭션은 데이터베이스의 작업을 처리하는 단위

### 트랜잭션의 특성

| 원자성(Atomicity) | - 트랜잭션은 데이터베이스 연산의 전부가 실행되거나 전혀 실행되지 않아야 한다
- 트랜잭션의 처리가 완전히 끝나지 않았을 경우는 실행되지 않은 상태와 같아야 한다 |
| --- | --- |
| 일관성(Consistency) | - 트랜잭션 실행 결과로 데이터베이스의 상태가 모순되지 않아야 한다
- 트랜잭션 실행 후에도 일관성이 유지되어야 한다 |
| 고립성(Isolation) | - 트랜잭션 실행 중에 생성하는 연산의 중간결과는 다른 트랜잭션이 접근할 수 없다
- 부분적인 실행 결과를 다른 트랜잭션이 볼 수 없다 |
| 영속성(Durability) | 트랜잭션이 그 실행을 성공적으로 완료하면 그 결과는 영구적 보장이 되어야 한다 |

### SQL문의 실행 순서

- 개발자가 작성한 SQL문(DDL, DML, DCL 등)은 3단계를 걸쳐서 실행된다
- SQL문의 문법을 검사하고 구문 분석을 한다
- 구문 분석 이후에 SQL을 실행
- SQL이 실행되면 데이터를 인출

| 파싱(Parsing) | - SQL문의 문법을 확인하고 구문 분석한다
- 구문 분석한 SQL문은 Library Cache에 저장한다 |
| --- | --- |
| 실행(Execution) | 옵티마이저(Optimizer)가 수립한 실행 계획에 따라 SQL을 실행한다 |
| 인출(Fetch) | 데이터를 읽어서 전송한다 |

# DDL

### 테이블(Table) 생성

- 데이터베이스를 사용하기 위해서는 테이블을 먼저 생성해야 한다
- 테이블 생성은 Create Table
- 테이블 변경은 Alter Table
- 테이블 삭제는 Drop Table

### 테이블 관리 SQL문

| Create Table  | - 새로운 테이블을 생성한다
- 테이블을 생성할 때 기본키, 외래키, 제약사항 등을 설정할 수 있다 |
| --- | --- |
| Alter Table  | - 생성된 테이블을 변경한다
- 컬럼을 추가하거나 변경, 삭제할 수 있다 |
| Drop Table | - 해당 테이블을 삭제한다
- 테이블의 데이터 구조뿐만 아니라 저장된 데이터도 모두 삭제된다 |

### 기본적인 테이블 생성

```sql
Create Table EMP
(
	empno number(10) primary key,
	ename varchar2(20),
	sal number(6)
);
```

### Create Table문의 구조

| Create Table | - Create Table EMP는 EMP 테이블을 생성하라는 의미
- ( ) 사이에 컬럼을 쓰고 마지막은 세미콜론으로 끝난다 |
| --- | --- |
| 컬럼 정보 | - 테이블에 생성되는 컬럼 이름과 데이터 타입을 입력한다
- 컬럼 이름은 영문, 한글, 숫자 모두 가능 |
| 데이터 타입 | - number는 컬럼의 데이터 타입을 숫자형 타입으로, varchar2는 가변 길이 문자열로 지정할 때 사용한다
- char는 컬럼의 데이터 타입을 고정된 크기의 문자로 지정할 때, date는 날짜형 타입으로 지정할 때 사용한다 |
| 기본키 | 기본키를 지정할 때 컬럼 옆에 primary key를 입력한다 |

### 테이블의 구조 확인

- SQL 중에 DESC문이 있다
- DESC문은 테이블의 구조를 확인할 때 사용된다
- Create Table로 생성된 테이블의 구조를 보고 싶을 때 사용한다

```sql
DESC EMP;
```

### 제약조건 사용

- 기본키, 외래키, 기본값, not null 등은 테이블을 생성할 때 지정할 수 있다

```sql
Create Table EMP(
	empno number(10),
	ename varchar2(20),
	sal number(10,2) default 0,
	deptno varchar2(4) not null,
	createdate date default sysdate,
	constraint emppk primary key(empno)
);
```

- constraint를 사용하여 기본키(empno)와 기본키의 이름(emppk)을 지정할 수 있다
- 두 개의 기본키를 지정하고자 한다면 constraint emppk primary key(empno, ename)으로 지정하면 된다
- number(10,2)은 소수점 둘째 자리까지 지정한다
- Oracle에서 sysdate는 오늘의 날짜를 조회한다. default 옵션을 사용해서 오늘 날짜를 기본값으로 지정할 수 있다

```sql
Create Table DEPT(
	deptno varchar2(4) primary key,
	deptname varchar2(20)
);
Create Table EMP(
	empno number(10),
	ename varchar2(20),
	sal number(10,2) default 0,
	deptno varchar2(4) not null,
	createdate date default sysdate,
	constraint emppk primary key(empno),
	constraint deptfk foreign key(deptno) references dept(deptno)
);
```

- 외래키(foreign key)를 지정하려면, 먼저 마스터 테이블이 생성되어야 한다
- EMP 테이블을 생성할 때 constraint를 사용하여 외래키 이름인 deptfk를 입력 후 외래키를 생성한다

```sql
constraint deptfk foreign key(deptno) references dept(deptno)
```

### 테이블 생성 시 CASCADE 사용

- 테이블을 생성할 때 CASCADE 옵션을 사용할 수 있다.
- CASCADE 옵션은 참조 관계(기본키와 외래키 관계)가 있을 경우 참조되는 데이터를 자동으로 반영할 수 있는 것이다
- 먼저, 마스터 테이블을 생성한다. 즉, DEPT 테이블을 생성하고 데이터를 입력한다

```sql
Create Table DEPT
(
	deptno varchar2(4) primary key,
	deptname varchar2(20)
);
Create Table EMP
(
	empno number(10),
	ename varchar2(20),
	sal number(10,2) default 0,
	deptno varchar2(4) not null,
	createdate date default sysdate,
	constraint e_pk primary key(empno),
	constraint d_fk foreign key(deptno) references dept(deptno) ON DELETE CASCADE
);
```

- ON DELETE CASCADE 옵션은 자신이 참조하고 있는 테이블(DEPT)의 데이터가 삭제되면 자동으로 자신(EMP)도 삭제되는 옵션이다
- ON DELETE CASCADE 옵션을 사용하면 참조 무결성을 준수할 수 있다

### 테이블명 변경

- 테이블명 변경은 ALTER TABLE ~ RENAME TO

```sql
ALTER TABLE EMP RENAME TO NEW_EMP;
//EMP 테이블을 NEW_EMP 테이블로 변경한다
```

### 컬럼 추가

- 생성된 EMP 테이블에 ALTER TABLE ~ ADD 문을 사용해서 컬럼을 추가 한다

```sql
ALTER TABLE EMP ADD (age number(2) default 1);
//EMP 테이블에 age 컬럼을 추가한다
```

### 컬럼 변경

- 컬럼 변경은 ALTER TABLE ~ MODIFY
- 컬럼 변경을 통해 데이터 타입을 변경하거나 데이터의 길이를 변경할 수 있다
- 컬럼을 변경할 때 제약조건을 설정할 수도 있다
- 컬럼의 데이터 타입을 변경할 때 기존 데이터가 있는 경우 에러가 발생한다

```sql
ALTER TABLE EMP MODIFY (ename varchar2(40) not null);
//EMP 테이블에 ename 컬럼의 길이를 20에서 40으로 변경하고 Not Null 조건을 설정
```

### 컬럼 삭제

- 컬럼 삭제는 ALTER TABLE ~ DROP COLUMN

```sql
ALTER TABLE EMP DROP COLUMN age;
//EMP 테이블에 age 컬럼을 삭제한다
```

### 컬럼명 변경

- 컬럼명 변경은 ALTER TABLE ~ RENAME COLUMN ~ TO

```sql
ALTER TABLE EMP RENAME COLUMN ename to new_ename;
//EMP 테이블에 ename 컬럼명을 new_ename으로 변경한다
```

### 테이블 삭제

- 테이블 삭제는 DROP TABLE
- DROP TABLE은 테이블의 구조와 데이터를 모두 삭제한다
- DROP TABLE에서 CASCADE CONTRAINT 옵션을 사용할 수 있다
- CASCADE CONTRAINT 옵션은 해당 테이블의 데이터를 외래키로 참조한 슬레이브 테이블과 관련된 제약사항도 삭제할 때 사용된다

```sql
DROP TABLE EMP;
//EMP 테이블의 데이터와 테이블의 구조를 모두 삭제한다
DROP TABLE EMP CASCADE CONTRAINT;
//참조된 제약사항까지도 모두 삭제한다
```

### 뷰(View) 생성과 삭제

- 뷰란 테이블로부터 유도된 가상의 테이블
- 실제 데이터를 가지고 있지 않고 테이블을 참조해서 원하는 컬럼만을 조회할 수 있게 한다
- 뷰는 데이터 딕셔너리(Data Dictionary)에 SQL문 형태로 저장하되 실행 시에 참조된다

### 뷰의 특징

- 참조한 테이블이 변경되면 뷰도 변경된다
- 뷰의 검색은 참조한 테이블과 동일하게 할 수 있지만, 뷰에 대한 입력, 수정, 삭제에는 제약이 있다
- 특정 컬럼만 조회시켜서 보안성을 향상시킨다
- 한번 생성된 뷰는 변경할 수 없고 변경을 원하면 삭제 후 재생성해야 한다
- ALTER문을 사용해서 뷰를 변경할 수 없다

### 뷰 생성

- 뷰를 생성할 때 CREATE VIEW문을 사용하며 이때 참조할 테이블은 SELECT문으로 지정한다

```sql
CREATE VIEW T_EMP AS SELECT * FROM EMP;
//EMP 테이블을 조회해서 그 결과로 T_EMP라는 뷰(View)로 생성한다
```

### 뷰 조회

- 뷰의 조회는 SELECT문을 사용해서 일반 테이블처럼 조회한다

```sql
SELECT * FROM T_EMP;
//뷰를 조회
```

### 뷰 삭제

- 뷰의 삭제는 DROP VIEW
- 뷰를 삭제했다고 해서 참조했던 테이블이 삭제되지 않는다

```sql
DROP VIEW T_EMP;
//뷰 삭제
```

### 뷰의 장점과 단점

| 장점 | 단점 |
| --- | --- |
| - 특정 컬럼만 조회할 수 있기 때문에 보안 기능이 있다
- 데이터 관리가 간단하다
- SELECT문이 간단해진다
- 하나의 테이블에 여러 개의 뷰를 생성할 수 있다 | - 뷰는 독자적인 인덱스를 만들 수 없다
- 삽입, 수정, 삭제 연산이 제약된다
- 데이터 구조를 변경할 수는 없다 |

# DML

### INSERT 문

- 테이블에 데이터를 입력하는 DML문이다

```sql
INSERT INTO table (column1, column2, ...) VALUES (ex1, ex2, ...);
```

- EMP 테이블에 데이터를 삽입하려면 테이블명, 컬럼명, 데이터 순으로 입력
- 데이터를 입력할 때 문자열을 입력하는 경우에는 작은따옴표(’ ‘)를 사용한다
- 만약 특정 테이블의 모든 컬럼에 대한 데이터를 삽입하는 경우에는 컬럼명을 생략할 수 있다
- 모든 컬럼에 데이터를 입력한다

```sql
INSERT INTO EMP VALUES(1000,'임베스트');
```

- 위에 예처럼 컬럼명을 생략할 수 있다. 단, 위의 예에서 테이블의 컬럼은 숫자형 데이터 타입 한 개의 컬럼과 문자형 데이터 타입 한 개의 컬럼만 있어야 한다
- INSERT문을 실행했다고 데이터 파일에 저장되는 것은 아니다. 최종적으로 데이터를 저장하려면 TCL문인 Commit을 실행해야 한다
- 만약 Auto Commit(Set auto commit on)으로 설정된 경우에는 Commit을 실행하지 않아도 바로 저장된다

### SELECT문으로 입력

- SELECT문을 사용하여 데이터를 조회해서 해당 테이블에 바로 삽입할 수 있다
- 단, 입력되는 테이블은 사전에 생성되어 있어야 한다

```sql
INSERT INTO DEPT_TEST SELECT * FROM DEPT;
//DEPT 테이블의 모든 데이터를 조회해서 DEPT_TEST 테이블에 입력한다
```

### Nologging 사용

- 데이터베이스에 데이터를 입력하면 로그파일(Log file)에 그 정보를 기록한다
- Check point라는 이벤트가 발생하면 로그파일의 데이터를 데이터 파일에 저장한다
- Nologging 옵션은 로그파일의 기록을 최소화시켜서 입력 시 성능을 향상시키는 방법이다
- Nologging 옵션은 Buffer Cache라는 메모리 영역을 생략하고 기록한다

```sql
ALTER TABLE DEPT NOLOGGING;
//로그파일의 기록을 최소화하여 입력 성능을 향상시킨다
```

### UPDATE문

- 입력된 데이터의 값을 수정하려면, UPDATE문을 사용한다
- UPDATE문을 사용하여 원하는 조건으로 데이터를 검색해서 해당 데이터를 수정할 수 있다
- 만약, UPDATE문에 조건문을 입력하지 않으면 모든 데이터가 수정되므로 유의해야 한다

```sql
UPDATE EMP SET ENAME='조조' WHERE EMPNO=100;
```

- UPDATE문에서 주의사항은 데이터를 수정할 때 조건절에서 검색되는 행 수만큼 수정된다는 것이다

### DELETE문

- DELETE문은 원하는 조건을 검색해서 해당되는 행을 삭제한다
- DELETE문에 조건문을 입력하지 않으면 모든 데이터가 삭제된다. 즉, 테이블에 있는 모든 데이터가 삭제되는 것이다
- DELETE문으로 데이터를 삭제한다고 해서 테이블의 용량이 초기화되지는 않는다

```sql
DELETE FROM EMP WHERE EMPNO=100;
//EMP 테이블에서 EMPNO가 100번인 직원을 삭제한다
```

- 만약 위의 예에서 WHERE절(조건)을 입력하지 않으면 EMP 테이블의 모든 데이터가 삭제된다

### 테이블의 모든 데이터 삭제

| DELETE FROM 테이블명; | TRUNCATE TABLE 테이블명; |
| --- | --- |
| - 테이블의 모든 데이터를 삭제한다
- 데이터가 삭제되어도 테이블의 용량은 감소하지 않는다 | - 테이블의 모든 데이터를 삭제한다
- 데이터가 삭제되면 테이블의 용량은 초기화된다 |
- TRUNCATE TABLE EMP는 EMP 테이블의 모든 데이터를 삭제하면서 테이블의 용량이 초기화된다

### SELECT문 사용

- 테이블에 입력된 데이터를 조회하기 위해서 SELECT문을 사용한다
- SELECT문은 특정 컬럼이나 특정 행만을 조회할 수 있다

```sql
SELECT * FROM EMP WHERE 사원번호=1000;
```

- 위의 SELECT문에서 EMP 테이블의 모든 컬럼 ‘*’을 출력한다
- 단, WHERE절에 있는 조건문에 있는 행만 조회한다

### SELECT 문법

| SELECT * | - 모든 컬럼을 출력한다
- ‘*’는 모든 컬럼을 의미한다 |
| --- | --- |
| FROM EMP | - FROM절에는 테이블명을 쓴다
- 즉, EMP 테이블을 지정한다 |
| WHERE 사원번호=1000 | - EMP 테이블에서 사원번호가 1000번인 행을 조회한다
- 즉, 조건문을 지정한다 |

### SELECT 컬럼 지정

| SELECT EMPNO, ENAME FROM EMP | EMP 테이블의 모든 행에서 EMPNO와 ENAME 컬럼만 출력한다 |
| --- | --- |
| SELECT * FROM EMP | EMP 테이블의 모든 컬럼과 모든 행을 조회한다 |
| SELECT ENAME || ‘님’ FROM EMP | - EMP 테이블의 모든 행에서 ENAME 컬럼을 조회한다
- 단, ENAME 컬럼 뒤에 ‘님’이라는 문자를 결합한다 |

### ORDER BY를 사용한 정렬

- SELECT문을 사용할 때 ORDER BY를 같이 사용할 수 있다
- ORDER BY는 데이터를 오름차순 혹은 내림차순으로 출력한다
- ORDER BY가 정렬을 하는 시점은 모든 실행이 끝난 후에 데이터를 출력해 주기 바로 전이다
- ORDER BY는 정렬을 하기 때문에 데이터베이스 메모리를 많이 사용하게 된다. 즉, 대량의 데이터를 정렬하게 되면 정렬로 인한 성능 저하가 발생한다
- Oracle 데이터베이스는 정렬을 위해서 메모리 내부에 할당된 SORT_AREA_SIZE를 사용한다. 만약 SORT_AREA_SIZE가 너무 작으면 성능 저하가 발생한다
- 정렬을 회피하기 위해서 인덱스(Index)를 생성할 때 사용자가 원하는 형태로 오름차순 혹은 내림차순으로 생성해야 한다
- 특별한 지정이 없으면 ORDER BY는 오름차순으로 정렬한다

```sql
SELECT * FROM EMP ORDER BY ENAME, SAL DESC;
//ENAME으로 오름차순 정렬하고 SAL로 내림차순 정렬한다
```

- 기본적으로 오름차순과 내림차순을 지정하지 않으면 오름차순으로 정렬한다

### Index를 사용한 정렬 회피

- 정렬은 Oracle 데이터베이스에 부하를 주므로, 인덱스를 사용해서 Order by를 회피할 수 있다

```sql
SELECT /*+ INDEX_DESC(A) */ FROM EMP A;
```

- /*+ INDEX_DESC(A) */ 를 사용했다. EMP 테이블에 생성된 인덱스를 내림차순으로 읽게 지정한 것이다

### DISTINCT와 Alias

- DISTINCT문은 컬럼명 앞에 지정하여 중복된 데이터를 한 번만 조회하게 한다

```sql
SELECT DISTINCT DEPTNO FROM EMP
```

- DISTINCT를 사용하면 DEPTNO 값이 중복되지 않는다
- Alias(별칭)은 테이블명이나 컬럼명이 너무 길어서 간략하게 할 때 사용한다

```sql
SELECT ENAME AS "이름" FROM EMP a WHERE a.EMPNO=1000;
```

## WHERE문 사용

### 비교 연산자

| = | 같은 것을 조회 |
| --- | --- |
| < | 작은 것을 조회 |
| ≤ | 작거나 같은 것을 조회 |
| > | 큰 것을 조회 |
| ≥ | 크거나 같은 것을 조회 |

### 부정 비교 연산자

| ≠ | 같지 않은 것을 조회 |
| --- | --- |
| ^= | 같지 않은 것을 조회 |
| <> | 같지 않은 것을 조회 |
| NOT 컬럼명 = | 같지 않은 것을 조회 |
| NOT 컬럼명 > | 크지 않은 것을 조회 |

### 논리 연산자

| AND | 조건을 모두 만족해야 참(True)이 된다 |
| --- | --- |
| OR | 조건 중 하나만 만족해도 참(True)이 된다 |
| NOT | 참이면 거짓(False)으로 바꾸고 거짓이면 참(True)으로 바꾼다 |

### SQL 연산자

| LIKE ‘%비교문자열%’ | 비교 문자열을 조회한다. %는 모든 값을 의미 |
| --- | --- |
| BETWEEN A AND B | A와 B 사이의 값을 조회한다 |
| IN (list) | OR을 의미하며 list 값 중에 하나만 일치해도 조회된다 |
| IS NULL | NULL 값을 조회한다 |

### 부정 SQL 연산자

| NOT BETWEEN A AND B | A와 B 사이의 해당되지 않는 값을 조회한다 |
| --- | --- |
| NOT IN (list) | list와 불일치한 것을 조회한다 |
| IS NOT NULL | NULL 값이 아닌 것을 조회한다 |

```sql
SELECT * FROM EMP 
WHERE EMPNO=1001 AND SAL >= 1000;
//EMP 테이블에서 EMPNO가 1001이고 SAL이 1000보다 크거나 같은 것을 조회한다
```

## LIKE문 사용

- LIKE문은 와일드카드를 사용해서 데이터를 조회할 수 있다

### 와일드카드

| % | - 어떤 문자를 포함한 모든 것을 조회한다
- 예를 들어 ‘조%’는 ‘조’로 시작하는 모든 문자를 조회한다 |
| --- | --- |
| _ | 한 개인 단일 문자를 의미한다 |

```sql
SELECT * FROM EMP
WHERE ENAME LIKE 'test%';
//ENAME이 'test'로 시작하는 모든 데이터를 조회한다

SELECT * FROM EMP
WHERE ENAME LIKE '%1';
//ENAME의 마지막이 '1'로 끝나는 모든 것을 조회한다

SELECT * FROM EMP
WHERE ENAME LIKE '%est%';
//ENAME의 중간에 'est'가 있는 모든 것을 조회한다

SELECT * FROM EMP
WHERE ENAME LIKE 'test1';
//LIKE문에 와일드카드를 사용하지 않으면 '='와 같다

SELECT * FROM EMP
WHERE ENAME LIKE 'test_';
//ENAME 컬럼에서 'test'로 시작하고 하나의 글자만 더 있는 것을 조회한다
```

### BETWEEN문 사용

- BETWEEN문은 지정된 범위에 있는 값을 조회한다

```sql
SELECT * FROM EMP
WHERE SAL BETWEEN 1000 AND 2000;
//SAL이 1000이상 2000이하 사이의 값을 조회한다

SELECT * FROM EMP
WHERE SAL NOT BETWEEN 1000 AND 2000;
//SAL이 1000미만 2000 초과인 값을 조회한다
```

### IN문 사용

- IN문은 “OR”의 의미를 가지고 있어서 하나의 조건만 만족해도 조회가 된다

```sql
SELECT * FROM EMP
WHERE JOB IN ('CLERK', 'MANAGER');
//IN은 OR의 의미를 가진다. 그래서 JOB 컬럼이 
//'CLERK'이거나 'MANAGER'인 레코드를 조회한다

SELECT * FROM EMP
WHERE (JOB, ENAME)
IN (('CLERK', 'test1'), ('MANAGER', 'test4'));
//IN 조건에 두 개의 컬럼을 지정한다
```

### NULL의 특징

- NULL은 모르는 값을 의미한다
- NULL은 값의 부재를 의미한다
- NULL과 숫자 혹은 날짜를 더하면 NULL이 된다
- NULL과 어떤 값을 비교할 때, ‘알 수 없음’이 반환된다

### NULL 값 조회

- NULL을 조회할 경우는 IS NULL을 사용하고 NULL 값이 아닌 것을 조회할 경우는 IS NOT NULL을 사용한다

```sql
SELECT * FROM EMP
WHERE MGR IS NOT NULL;
//NULL 값이 아닌 것을 조회한다
```

### NULL 관련 함수

| NVL 함수(Oracle) | - NULL이면 다른 값으로 바꾸는 함수이다
- ‘NVL(MGR, 0)’은 MGR 컬럼이 NULL이면 0으로 바꾼다 |
| --- | --- |
| NVL2 함수(Oracle) | - NVL 함수와 DECODE 함수를 하나로 만든 것이다
- ‘NVL2(MGR, 1, 0)’은 MGR컬럼이 NULL이 아니면 1을, NULL이면 0을 반환한다 |
| NULLIF 함수(Oracle, MS-SQL, MySQL) | - 두 개의 값이 같으면 NULL을, 같지 않으면 첫 번째 값을 반환한다
- ‘NULLIF(exp1, exp2)’은 exp1과 exp2가 같으면 NULL을, 같지 않으면 exp2를 반환한다 |
| COALESCE(Oracle, MS-SQL) | - NULL이 아닌 최초의 인자 값을 반환한다
- ‘COALESCE(exp1, exp2, exp3, …)’은 exp1이 NULL이 아니면 exp1의 값을, 그렇지 않으면 그 뒤의 값의 NULL 여부를 판단하여 값을 반환한다 |

### GROUP BY문

- GROUP BY는 테이블에서 소규모 행을 그룹화하여 합계, 평균, 최대값, 최소값 등을 계산할 수 있다
- HAVING구에 조건문을 사용한다
- Grouping된 결과에 대한 조건문을 사용한다
- ORDER BY를 사용해서 정렬을 할 수 있다

```sql
SELECT DEPTNO, SUM(SAL)
FROM EMP
GROUP BY DEPTNO;
//DEPTNO로 그룹을 만들고 그룹별 합계를 계산
```

### HAVING문 사용

- GROUP BY에 조건절을 사용하려면 HAVING을 사용해야 한다. 만약 WHERE절에 조건문을 사용하게 되면 조건을 충족하지 못하는 데이터들은 GROUP BY 대상에서 제외된다

```sql
SELECT DEPTNO, SUM(SAL)
FROM EMP
GROUP BY DEPTNO
HAVING SUM(SAL) >10000;
//GROUP BY 결과에서 급여합계가 10000 이상만 조회한다
```

### 집계 함수 종류

| COUNT() | 행 수를 조회 |
| --- | --- |
| SUM() | 합계를 계산 |
| AVG() | 평균을 계산 |
| MAX()와 MIN() | 최대값과 최소값을 계산 |
| STDDEV() | 표준편차를 계산 |
| VARIANCE() | 분산을 계산 |

### COUNT 함수

- COUNT() 함수는 행 수를 계산하는 함수이다. COUNT(*)는 NULL 값을 포함한 모든 행 수를 계산한다. 하지만 COUNT(컬럼명)는 NULL 값을 제외한 행 수를 계산한다

```sql
SELECT COUNT(*) FROM EMP;
//NULL을 포함한 전체 행 수를 계산한다
```

- MGR 컬럼은 한 개의 NULL을 가지고 있다. 그래서 COUNT(MGR)로 하면 NULL이 제외되고 행 수를 계산한다

```sql
SELECT COUNT(MGR) FROM EMP;
//NULL을 제외한 전체 행 수를 계산한다
```

## GROUP BY 사용 예제

### 부서별(DEPTNO), 관리자별(MGR) 급여평균 계산

- 부서별, 관리자별 급여평균이므로 GROUP BY에 부서와 관리자를 추가한다
- 평균을 계산하기 위해서 SELECT문에 AVG 함수를 사용해야 한다

```sql
SELECT DEPTNO, MGR, AVG(SAL)
FROM EMP
GROUP BY DEPTNO, MGR;
```

### 직업별(JOB) 급여합계 중에 급여(SAL)합계가 1000 이상인 직업

- 직업별 급여합계이므로 GROUP BY에 JOB을 포함시키고 급여합계가 1000 이상만 조회해야 하므로 HAVING구에 조건을 넣어야 한다

```sql
SELECT JOB, SUM(SAL)
FROM EMP
GROUP BY JOB
HAVING SUM(SAL) >=1000;
```

### 사원번호 1000~1003번의 부서별 급여합계

- 사원번호 1000번에서 1003번까지 조회를 해야 하므로 WHERE문에 조건을 넣어야 한다
- 그리고 부서별 합계이므로 GROUP BY에 DEPTNO를 사용하고 SELECT문에 SUM 함수를 사용한다

```sql
SELECT DEPTNO, SUM(SAL) FROM EMP
WHERE EMPNO BETWEEN 1000 AND 1003
GROUP BY DEPTNO;
```

### SELECT문 실행 순서

```sql
SELECT ename //5
FROM emp //1
WHERE empno=10 //2
GROUP BY ename //3
HAVING count(*) >=1 //4
ORDER BY ename; //6
```

### 명시적(Explicit) 형변환과 암시적(Implicit) 형변환

- 형변환은 두 개의 데이터의 데이터 타입(형)이 일치하도록 변환하는 것이다
- 예를 들어 숫자와 문자열의 비교, 문자열과 날짜형의 비교와 같이 데이터 타입이 불일치할 때 발생한다
- 형변환은 명시적(Explicit) 형변환과 암시적(Implicit) 형변환이 있다
- 명시적 형변환은 형변환 함수를 사용해서 데이터 타입을 일치시키는 것으로 개발자가 SQL을 사용할 때 형변환 함수를 사용해야 한다

### 형변환 함수

| TO_NUMBER(문자열) | 문자열을 숫자로 변환한다 |
| --- | --- |
| TO_CHAR(숫자 혹은 날짜, [FORMAT]) | 숫자 혹은 날짜를 지정된 FORMAT의 문자로 변환한다 |
| TO_DATE(문자열, FORMAT) | 문자열을 지정된 FORMAT의 날짜형으로 변환한다 |
- 암시적 형변환은 개발자가 형변환을 하지 않은 경우 데이터베이스 관리 시스템이 자동으로 형변환하는 것을 의미한다

### 인덱스 컬럼에 형변환을 수행하면 인덱스를 사용하지 못한다

- 인덱스는 데이터를 빠르게 조회하기 위해서 인덱스 키를 기준으로 정렬해 놓은 데이터이다
- 그런데 인덱스는 기본적으로 변형이라는 것이 발생하면 인덱스를 사용할 수 없다. 물론 예외적인 것도 있다
- 따라서 인덱스가 있어도 인덱스 컬럼에 형변환이 발생하면 인덱스를 사용할 수 없다

### 내장형 함수

- 모든 데이터베이스는 SQL에서 사용할 수 있는 내장형 함수를 가지고 있다
- 내장형 함수는 데이터베이스 관리 시스템 벤더별로 약간의 차이가 있지만, 거의 비슷한 방법으로 사용이 가능하다
- 내장형 함수로는 형변환 함수, 문자열 및 숫자형 함수, 날짜형 함수가 있다

### DUAL 테이블

- DUAL 테이블은 Oracle 데이터베이스에 의해서 자동으로 생성되는 테이블이다
- Oracle 데이터베이스 사용자가 임시로 사용할 수 있는 테이블로 내장형 함수를 실행할 때도 사용할 수 있다
- Oracle 데이터베이스의 모든 사용자가 사용할 수 있다

### 내장형 함수의 종류

- ASCII 함수는 문자에 대한 ASCII 코드 값을 알려준다. ASCII 코드는 대문자 A를 기준으로 A(65), B(66), C(67) 등의 값이다
- SUBSTR 함수는 지정된 위치의 문자열을 자르는 함수이고 LENGTH 함수, LEN 함수는 문자열의 길이를 계산한다
- LTRIM 함수를 사용하면 문자열의 왼쪽 공백을 제거할 수 있다
- 또한 함수를 중첩해서 사용해도 된다(ex: LENGTH(LTRIM(’ ABC’)))

```sql
SELECT ASCII('a'), SUBSTR('ABC',1,2),
			 LENGTH('A BC'), LTRIM(' ABC'),
			 LENGTH(LTRIM(' ABC'))
FROM DUAL;
```

### 문자열 함수

| ASCII(문자) | 문자 혹은 숫자를 ASCII 코드값을 변환한다 |
| --- | --- |
| CHR(ASCII 코드값) | ASCII 코드값을 문자로 변환한다 |
| SUBSTR(문자열,m,n) | 문자열에서 m번째 위치부터 n개를 자른다 |
| CONCAT(문자열1,문자열2) | - 문자열1번과 문자열2번을 결합한다
- Oracle은 ‘||’, MS-SQL은 ‘+’을 사용할 수 있다 |
| LOWER(문자열) | 영문자를 소문자로 변환한다 |
| UPPER(문자열) | 영문자를 대문자로 변환한다 |
| LENGTH 혹은 LEN(문자열) | 공백을 포함해서 문자열의 길이를 알려준다 |
| LTRIM(문자열, 지정문자) | - 왼쪽에서 지정된 문자를 삭제한다
- 지정된 문자를 생략하면 공백을 삭제한다 |
| RTRIM(문자열, 지정문자) | - 오른쪽에서 지정된 문자를 삭제한다
- 지정된 문자를 생략하면 공백을 삭제한다 |
| TRIM(문자열, 지정된 문자) | - 왼쪽 및 오른쪽에서 지정된 문자를 삭제한다
- 지정된 문자를 생략하면 공백을 삭제한다 |
- 날짜형 함수 중에서 오늘 날짜를 구하기 위해서는 SYSDATE를 사용하면 된다
- 만약, 해당 연도만 알고 싶다면, EXTRACT 함수를 사용한다
- TO_CHAR 함수는 형변환 함수 중에서 가장 많이 사용하는 것으로 숫자나 날짜를 원하는 포맷의 문자열로 변환한다

```sql
SELECT 
	SYSDATE,
	EXTRACT(YEAR FROM sysdate),
	TO_CHAR(SYSDATE, 'YYYYMMDD')
FROM DUAL;
```

### 날짜형 함수

| SYSDATE | 오늘의 날짜를 날짜 타입으로 알려준다 |
| --- | --- |
| EXTRACT(YEAR FROM SYSDATE) | 날짜형 데이터에서 연도를 추출 |

```sql
SELECT 
	ABS(-1), SIGN(10),
	MOD(4,2), CEIL(10.9), FLOOR(10.1),
	ROUND(10.222,1)
FROM DUAL;
```

### 숫자형 함수

| ABS(숫자) | 절대값을 돌려준다 |
| --- | --- |
| SIGN(숫자) | 양수, 음수, 0을 구별한다 |
| MOD(숫자1, 숫자2) | - 숫자1을 숫자2로 나누어 나머지를 계산한다
- %를 사용해도 된다 |
| CEIL/CEILING(숫자) | 숫자보다 크거나 같은 최소의 정수를 돌려준다 |
| FLOOR(숫자) | 숫자보다 작거나 같은 최대의 정수를 돌려준다 |
| ROUND(숫자, m) | - 소수점 m 자리에서 반올림한다
- m의 기본값(Default Value)은 0이다 |
| TRUNC(숫자, m) | - 소수점 m 자리에서 절삭한다
- m의 기본값(Default Value)은 0이다 |

### DECODE

- DECODE문으로 IF문을 구현할 수 있다. 즉, 특정 조건이 참이면 A, 거짓이면 B로 응답한다

```sql
SELECT DECODE(EMPNO, 1000, 'TRUE', 'FALSE')
FROM EMP;
//EMPNO를 1000과 비교해서 같으면 TRUE출력 다르면 FALSE출력
```

### CASE문

- CASE문은 IF~THEN~ELSE-END의 프로그래밍 언어처럼 조건문을 사용할 수 있다
- 조건을 WHEN구에 사용한다. 해당 조건이 참이면 THEN이 실행되고 거짓이면 ELSE구가 실행된다

```sql
CASE [expression]
	WHEN condition_1 THEN result_1
	WHEN condition_2 THEN result_2
	...
	WHEN condition_n THEN result_n
	ELSE result
END

SELECT 
	CASE
		WHEN EMPNO=1000 THEN 'A'
		WHEN EMPNO=1001 THEN 'B'
		ELSE 'C'
	END
FROM EMP;
//EMPNO가 1000이면 A를 출력하고 1001이면 B를 출력한다
//만약 그렇지 않으면 C를 출력한다
```

### ROWNUM

- ROWNUM은 ORACLE 데이터베이스의 SELECT문 결과에 대해서 논리적인 일련번호를 부여한다
- ROWNUM은 조회되는 행 수를 제한할 때 많이 사용된다
- ROWNUM은 화면에 데이터를 출력할 때 부여되는 논리적 순번이다. 만약 ROWNUM을 사용해서 페이지 단위 출력을 하기 위해서는 인라인 뷰(Inline view)를 사용해야 한다

### 인라인뷰(Inline view)

- 인라인뷰는 SELECT문에서 FROM절에 사용되는 서브쿼리(Sub Query)를 의미한다

```sql
SELECT * FROM //Main Query
(SELECT * FROM EMP) a; //Sub Query(Inline view)
```

### SQL Server의 TOP 구문과 MySQL의 limit 구문

- Oracle은 ROWNUM을 사용하지만 SQL Server는 TOP문을 사용하고 MySQL은 LIMIT구를 사용한다. 즉, 10명만 출력하고자 할 때에는 다음과 같이 사용한다

```sql
SELECT TOP(10) FROM EMP;//SQL Server

SELECT * FROM EMP LIMIT 10; //MySQL
```

### ROWID

- ROWID는 ORACLE 데이터베이스 내에서 데이터를 구분할 수 있는 유일한 값이다
- ROWID는 SELECT ROWID, EMPNO FROM EMP와 같은 SELECT문으로 확인할 수 있다
- ROWID를 통해서 데이터가 어떤 데이터 파일, 어느 블록에 저장되어 있는지 알 수 있다

### ROWID 구조

| 구조 | 길이 | 설명 |
| --- | --- | --- |
| 오브젝트 번호 | 1~6 | 오브젝트(Object) 별로 유일한 값을 가지고 있으며, 해당 오브젝트가 속해 있는 값이다 |
| 상대 파일 번호 | 7~9 | 테이블스페이스(Tablespace)에 속해 있는 데이터 파일에 대한 상대 파일번호이다 |
| 블록 번호 | 10~15 | 데이터 파일 내부에서 어느 블록에 데이터가 있는지 알려준다 |
| 데이터 번호 | 16~18 | 데이터 블록에 데이터가 저장되어 있는 순서를 의미한다 |

### WITH구문

- 서브쿼리를 사용해서 임시 테이블이나 뷰처럼 사용할 수 있는 구문이다
- 서브쿼리 블록에 별칭을 지정할 수 있다
- 옵티마이저는 SQL을 인라인 뷰나 임시 테이블로 판단한다

```sql
WITH viewData AS
	(
		SELECT * FROM EMP
		UNION ALL
		SELECT * FROM EMP
	)
SELECT * FROM viewData WHERE EMPNO=1000;
```

# DCL

### GRANT

- GRANT문은 데이터베이스 사용자에게 권한을 부여한다
- 데이터베이스 사용을 위해서는 권한이 필요하며 연결, 입력, 수정, 삭제, 조회를 할 수 있다

```sql
GRANT privileges ON object TO user;
//privileges는 권한을 의미하며 object는 테이블명이다
//user는 Oracle 데이터베이스 사용자를 지정하면 된다
```

### Privileges(권한)

| SELECT | 지정된 테이블에 대해서 SELECT 권한을 부여한다 |
| --- | --- |
| INSERT | 지정된 테이블에 대해서 INSERT 권한을 부여한다 |
| UPDATE | 지정된 테이블에 대해서 UPDATE 권한을 부여한다 |
| DELETE | 지정된 테이블에 대해서 DELETE 권한을 부여한다 |
| REFERENCES | 지정된 테이블을 참조하는 제약조건을 생성하는 권한을 부여한다 |
| ALTER | 지정된 테이블에 대해서 수정할 수 있는 권한을 부여한다 |
| INDEX | 지정된 테이블에 대해서 인덱스를 생성할 수 있는 권한을 부여한다 |
| ALL | 테이블에 대한 모든 권한을 부여한다 |

```sql
GRANT SELECT, INSERT, UPDATE, DELETE
ON EMP
TO LIMBEST;
/*
LIMBEST 사용자에게 EMP 테이블에 대해서 
SELECT, INSERT, UPDATE, DELETE 권한을 부여한다
*/
```

### WITH GRANT OPTION과 ADMIN OPTION

| WITH GRANT | - 특정 사용자에게 권한을 부여할 수 있는 권한을 부여한다
- 권한을 A 사용자가 B에 부여하고 B가 다시 C를 부여한 후에 권한을 취소(Revoke)하면 모든 권한이 회수된다 |
| --- | --- |
| WITH ADMIN OPTION | - 테이블에 대한 모든 권한을 부여한다
- 권한을 A 사용자가 B에 부여하고 B가 다시 C에게 부여한 후에 권한을 취소(Revoke)하면 B 사용자 권한만 취소된다 |

```sql
GRANT SELECT, INSERT, UPDATE, DELETE
ON EMP
TO LIMBEST WITH GRANT OPTION;
//권한을 부여할 수 있는 권한을 부여한다
```

### REVOKE

- REVOKE문은 데이터베이스 사용자에게 부여된 권한을 회수한다

```sql
REVOKE privileges ON object FROM user;
```

# TCL

### COMMIT

- INSERT, UPDATE, DELETE문으로 변경한 데이터를 데이터베이스에 반영한다
- 변경 이전 데이터는 잃어버린다. 즉, A 값을 B로 변경하고 COMMIT을 하면 A 값은 잃어버리고 B 값을 반영한다
- 다른 모든 데이터베이스 사용자는 변경된 데이터를 볼 수 있다
- COMMIT이 완료되면 데이터베이스 변경으로 인한 LOCK이 해제(UNLOCK)된다
- COMMIT이 완료되면 다른 모든 데이터베이스 사용자는 변경된 데이터를 조작할 수 있다
- COMMIT을 실행하면 하나의 트랜잭션 과정을 종료한다
- Oracle 데이터베이스는 암시적 트랜잭션 관리를 한다. 즉, Oracle 데이터베이스로 트랜잭션을 시작하고 트랜잭션의 종료는 Oracle 데이터베이스 사용자가 COMMIT 혹은 ROLLBACK으로 처리해야 한다

### Auto commit

- SQL*PLUS 프로그램을 정상적으로 종료하는 경우 자동 COMMIT 된다
- DDL 및 DCL을 사용하는 경우 자동 COMMIT 된다
- set autocommit on; 을 SQL*PLUS에서 실행하면 자동 COMMIT된다

### ROLLBACK

- ROLLBACK을 실행하면 데이터에 대한 변경 사용을 모두 취소하고 트랜잭션을 종료한다
- INSERT, UPDATE, DELETE문의 작업을 모두 취소한다. 단, 이전에 COMMIT한 곳까지만 복구한다
- ROLLBACK을 실행하면 LOCK이 해제되고 다른 사용자도 데이터베이스 행을 조작할 수 있다

### SAVEPOINT(저장점)

- SAVEPOINT는 트랜잭션을 작게 분할하여 관리하는 것으로 SAVEPOINT를 사용하면 지정된 위치 이후의 트랜잭션만 ROLLBACK 할 수 있다
- SAVEPOINT의 지정은 SAVEPOINT <SAVEPOINT명>을 실행한다
- 지정된 SAVEPOINT까지만 데이터 변경을 취소하고 싶은 경우는 ROLLBACK TO <SAVEPOINT명>을 실행한다
- ROLLBACK을 실행하면 SAVEPOINT와 관계없이 데이터의 모든 변경사항을 저장하지 않는다

## EQUI(등가) JOIN(교집합)

### EQUI(등가) JOIN

- 조인은 여러 개의 릴레이션을 사용해서 새로운 릴레이션을 만드는 과정이다
- 조인의 가장 기본은 교집합을 만드는 것이다
- 두 개의 테이블 간에 일치하는 것을 조인한다

```sql
SELECT * FROM EMP, DEPT
WHERE EMP.DEPTNO=DEPT.DEPTNO;
// =로 두 개의 테이블을 연결한다

SELECT * FROM EMP, DEPT
WHERE EMP.DEPTNO=DEPT.DEPTNO
AND EMP.ENAME LIKE '임%'
ORDER BY ENAME;
//조인문에 추가 조건 및 정렬을 할 수 있다
```

### INNER JOIN

- EQUI JOIN과 마찬가지로 ISO 표준 SQL로 INNER JOIN이 있다. INNER JOIN은 ON문을 사용해서 테이블을 연결한다

```sql
SELECT * FROM EMP INNER JOIN DEPT
ON EMP.DEPTNO=DEPT.DEPTNO;
//INNER JOIN구로 테이블을 정의한다
//ON구를 사용해서 조인 조건을 넣는다

SELECT * FROM EMP INNER JOIN DEPT
ON EMP.DEPTNO=DEPT.DEPTNO
AND EMP.ENAME LIKE '임%'
ORDER BY ENAME;
//조인문에 추가 조건 및 정렬을 할 수 있다
```

- 해시 함수는 테이블을 해시 메모리에 적재한 후에 해시 함수로써 연결하는 방법이다
- 해시 조인은 EQUI JOIN만 사용 가능한 방법이다

### 해시 조인(HASH JOIN)

- 해시 조인은 먼저 선행 테이블을 결정하고 선행 테이블에서 주어진 조건(Where구)에 해당하는 행을 선택한다
- 해당 행이 선택되면 조인 키(Join Key)를 기준으로 해시 함수를 사용해서 해시 테이블을 메인 메모리에 생성하고 후행 테이블에서 주어진 조건에 만족하는 행을 찾는다
- 후행 테이블의 조인 키를 사용해서 해시 함수를 적용하여 해당 버킷을 검색한다

### INTERSECT 연산

- 두 개의 테이블에서 교집합을 조회한다
- 즉, 두 개의 테이블에서 공통된 값을 조회한다

```sql
SELECT DEPTNO FROM EMP
INTERSECT 
SELECT DEPTNO FROM DEPT;
//INTERSECT 연산은 두 개의 테이블에서 교집합을 조회한다
```

## Non-EQUI(비등가) JOIN

- Non-EQUI는 두 개의 테이블 간에 조인하는 경우 =을 사용하지 않고 >, <, ≥, ≤ 등을 사용한다
- 즉, Non-EQUI JOIN은 정확하게 일치하지 않는 것을 조인하는 것이다

## OUTER JOIN

- 두 개의 테이블 간에 교집합(EQUI JOIN)을 조회하고 한쪽 테이블에만 있는 데이터도 포함시켜서 조회한다
- 이때 왼쪽 테이블에만 있는 행도 포함하면 LETE OUTER JOIN이라고 하고 오른쪽 테이블의 행만 포함시키면 RIGHT OUTER JOIN이라고 한다
- FULL OUTER JOIN은 LEFT OUTER JOIN과 RIGHT OUTER JOIN 모두를 하는 것이다
- Oracle 데이터베이스에서는 OUTER JOIN을 할 때 (+) 기호를 사용해서 할 수 있다

```sql
SELECT * FROM DEPT, EMP
WHERE EMP.DEPTNO (+)=DEPT.DEPTNO;
//Oracle 데이터베이스 OUTER JOIN 방법이다
```

### LEFT OUTER JOIN과 RIGHT OUTER JOIN

- LEFT OUTER JOIN은 두 개의 테이블에서 같은 것을 조회하고 왼쪽 테이블에만 있는 것을 포함해서 조회된다

```sql
SELECT * FROM DEPT LEFT OUTER JOIN EMP
ON EMP.DEPTNO=DEPT.DEPTNO;
//LEFT OUTER JOIN을 수행한다
```

- RIGHT OUTER JOIN은 두 개의 테이블에서 같은 것을 조회하고 오른쪽 테이블에만 있는 것을 포함해서 조회된다

```sql
SELECT * FROM DEPT RIGHT OUTER JOIN EMP
ON EMP.DEPTNO=DEPT.DEPTNO;
```

### CROSS JOIN

- CROSS JOIN은 조인 조건구 없이 2개의 테이블을 하나로 조인한다
- 조인구가 없기 때문에 카테시안 곱이 발생한다
- CROSS JOIN은 FROM절에 CROSS JOIN구를 사용하면 된다

## UNION을 사용한 합집합 구현

### UNION

- 두 개의 테이블을 하나로 만드는 연산이다
- 즉, 2개의 테이블을 하나로 합치는 것이다. 주의사항은 두 개의 테이블의 컬럼 수, 컬럼의 데이터 형식 모두가 일치해야 한다. 만약 두 개의 테이블에 UNION 연산이 사용될 때 컬럼 수 혹은 데이터 형식이 다르면 오류가 발생한다
- UNION 연산은 두 개의 테이블을 하나로 합치면서 중복된 데이터를 제거한다
- 그래서 UNION은 정렬(Sort) 과정을 발생시킨다

```sql
SELECT DEPTNO FROM EMP
UNION
SELECT DEPTNO FROM EMP;
//UNION은 중복된 데이터를 제거하면서 테이블을 합친다
```

### UNION ALL

- 두 개의 테이블을 하나로 합치는 것이다
- UNION처럼 중복을 제거하거나 정렬을 유발하지 않는다

```sql
SELECT DEPTNO FROM EMP
UNION ALL
SELECT DEPTNO FROM EMP;
//UNION ALL은 단순하게 테이블을 합친다
```

### 차집합을 만드는 MINUS

- 두 개의 테이블에서 차집합을 조회한다
- 즉, 먼저 쓴 SELECT문에는 있고 뒤에 쓰는 SELECT문에는 없는 집합을 조회하는 것이다
- MS-SQL에서는 MINUS와 동일한 연산이 EXCEPT이다

```sql
SELCET DEPTNO FROM DEPT
MINUS 
SELECT DEPTNO FROM EMP;
//DEPT와 EMP를 MINUS 연산을 하면 DEPT에만 있는 행을 조회하는 것이다
```

## 계층형 조회(CONNECT BY)

- 계층형 조회는 Oracle 데이터베이스에서 지원하는 것으로 계층형으로 데이터를 조회할 수 있다
- 트리(Tree) 형태의 구조로 질의를 수행하는 것으로 START WITH구는 시작 조건을 의미하고 CONNECT BY PRIOR는 조인 조건이다. Root 노드로부터 하위 노드의 질의를 실행한다
- 계층형 조회에서 MAX(LEVEL)을 사용하여 최대 계층 수를 구할 수 있다. 즉, 계층형 구조에서 마지막 Leaf Node의 계층값을 구한다

```sql
SELECT MAX(LEVEL)
FROM Limbest.EMP
START WITH MGR IS NULL
CONNECT BY PRIOR EMPNO=MGR;
//PRIOR 키워드는 바로 직전에 출력된 행을 의미한다
```

### CONNECT BY 키워드

| LEVEL  | 검색 항목의 깊이를 의미한다. 즉, 계층구조에서 가장 상위 레벨이 1이 된다 |
| --- | --- |
| CONNECT BY ROOT | 계층 구조에서 가장 최상위 값을 표시한다 |
| CONNECT BY ISLEAF | 계층 구조에서 가장 최하위를 표시한다 |
| SYS CONNECT BY PATH | 계층 구조의 전체 전개 경로를 표시한다 |
| NOCYCLE | 순환 구조가 발생지점까지만 전개된다 |
| CONNECT BY ISCYCLE | 순환 구조 발생 지점을 표시한다 |
- CONNECT BY구는 순방향 조회와 역방향 조회가 있다. 순방향 조회는 부모 엔터티로부터 자식 엔터티를 찾아가는 검색을 의미하고, 역방향 조회는 자식 엔터티로부터 부모 엔터티를 찾아가는 검색이다

### 계층형 조회

| START WITH 조건 | 계층 전개의 시작 위치를 지정하는 것이다 |
| --- | --- |
| PRIOR 자식=부모 | 부모에서 자식방향으로 검색을 수행하는 순방향 전개이다 |
| PRIOR 부모=자식 | 자식에서 부모방향으로 검색을 수행하는 역방향 전개이다 |
| NOCYCLE | 데이터를 전개하면서 이미 조회된 데이터를 다시 조회되면 CYCLE이 형성된다. 이때 NOCYCLE은 사이클이 발생되지 않게 한다 |
| Order siblings by 컬럼명 | 동일한 LEVEL인 형제노드 사이에서 정렬을 수행한다 |

### Main query와 Subquery

- Subquery는 SELECT문 내에 다시 SELECT문을 사용하는 SQL문이다
- Subquery의 형태는 FROM구에 SELECT문을 사용하는 인라인 뷰(Inline View)와 SELECT문에 Subquery를 사용하는 스칼라 서브쿼리(Scala Subquery) 등이 있다
- WHERE구에 SELECT문을 사용하면 서브쿼리(Subquery)라고 한다

```sql
SELECT *
FROM EMP
WHERE DEPTNO=
	(
		SELECT DEPTNO FROM DEPT
		WHERE DEPTNO=10
	);
//WHERE구에 있는 SELECT문은 서브쿼리이고 괄호 내에 SELECT문을 사용한다
//서브쿼리 밖에 있는 SELECT문은 메인쿼리이다
```

- FROM구에 SELECT문을 사용하여 가상의 테이블을 만드는 효과를 얻을 수 있다
- 이렇게 FROM구에 SELECT문을 사용한 것이 인라인 뷰이다

### 단일 행 서브쿼리와 다중 행 서브쿼리

- 서브쿼리는 반환하는 행 수가 한 개인 것과 여러 개인 것에 따라서 단일 행 서브쿼리와 멀티 행 서브쿼리로 분류된다
- 단일 행 서브쿼리는 단 하나의 행만 반환하는 서브쿼리로 비교 연산자 =, <, ≤, ≥, <> 를 사용한다
- 다중 행 서브쿼리는 여러 개의 행을 반환하는 것으로 IN, ANY, ALL, EXISTS를 사용해야 한다

### 서브쿼리 종류(반환 행)

| 단일 행 서브쿼리
(Single row subquery) | - 서브쿼리를 실행하면 그 결과는 반드시 한 행만 조회된다
- 비교 연산자인 =, <, ≤, ≥, <>를 사용한다 |
| --- | --- |
| 다중 행 서브쿼리
(Multi row subquery) | - 서브쿼리를 실행하면 그 결과는 여러 개의 행이 조회된다
- 다중 행 비교 연산자인 IN, ANY, ALL, EXISTS를 사용한다 |

### 다중 행 비교 연산자

|  |  |
| --- | --- |
|  |  |
|  |  |
